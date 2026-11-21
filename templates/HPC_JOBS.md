# Running steps on a SLURM cluster

One analysis step is one job (or one job array). Steps run in the order listed in each project's "Continue on HPC" table.

## Job template

```bash
#!/bin/bash
#SBATCH -J <step>_<run_id>
#SBATCH -p <partition>
#SBATCH -c 16
#SBATCH --mem=64G
#SBATCH -t 24:00:00
#SBATCH -o logs/%x_%j.out
#SBATCH -e logs/%x_%j.err
set -euo pipefail
set -o noclobber                  # never overwrite an existing file
mkdir -p work/<step>              # parent folder; safe to repeat
OUT=work/<step>/<run_id>
mkdir "$OUT"                      # run folder only: fails if it exists, so a run folder is never reused
trap 'touch "$OUT/.FAILED"' ERR
micromamba run -n <env> <command> --out "$OUT"
sha256sum "$OUT"/* > "$OUT/SHA256SUMS"
touch "$OUT/.DONE"
```

Arrays (one task per sample, run or assembly):

```bash
#SBATCH --array=1-<N>%20
mapfile -t IDS < samples.txt
ID=${IDS[$((SLURM_ARRAY_TASK_ID-1))]}
```

Chain steps so the next one starts only after success:

```bash
j1=$(sbatch --parsable step1.sh)
sbatch --dependency=afterok:$j1 step2.sh
```

## Rules

- Create `logs/` before the first `sbatch`; SLURM does not create it.
- Download steps (AM01) run on a node with internet access (login or transfer node); many clusters lack internet access on compute nodes.

- Do not call `conda activate` inside job scripts. Use `micromamba run -n <env>` (or the cluster's module system).
- One environment file per project, with pinned versions.
- Every run writes to a new folder and ends with `.DONE` or `.FAILED`.
- Do not delete or overwrite outputs of earlier runs. Make a new run instead and note why.
- Keep the partition, account and paths in a local config file that is not committed.
