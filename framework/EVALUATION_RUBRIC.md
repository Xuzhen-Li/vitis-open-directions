# Evaluation rubric: F, N and E scores

Written 2026-11-21 (UTC+8), taken from the scoring rules of the grapevine example in [examples/vitis/RANKING.md](../examples/vitis/RANKING.md). [中文](EVALUATION_RUBRIC.zh.md)

A direction is scored only after its [gap audit](../templates/GAP_AUDIT_TEMPLATE.md) is filled in. Scores are set on one date and then frozen; every later change goes into the adjustment register.

## Three axes, each scored 1 to 3

- **Feasibility (F): can it be done with public data now?** 3 = all inputs are public and their accessions were checked in the archive APIs. 2 = inputs are public, but some need manual curation, are only partly suitable (for example gapped assemblies, or calibration data from one sample), or carry accessions not yet checked. 1 = depends on data that may not be public (phenotypes, recorded sex, documented dates). F is scored on the main paper of the direction; data needed only by a follow-up paper are named in the paper split.
- **Novelty (N): after the literature checks.** 3 = not found in the species. 2 = partly done, with a clear narrower gap remaining. 1 = mostly done, with only a small or technical gap remaining. Novelty is judged within the species only; a precedent in another species does not lower the score.
- **Effort (E), higher means less effort.** Each direction gives an effort range; the upper end of the range sets the score.

| Upper end of the estimated effort | E | Tier |
|---|---|---|
| 6 weeks or less for one person | 3 | Quick |
| more than 6 weeks, up to 4 months | 2 | Medium |
| more than 4 months, or a step with a stated high risk of having to start again (calibration, GPU training) | 1 | Large |

## Order

Directions are ranked by the **sum** F + N + E (not the product), highest first. Equal totals are broken in this order: (a) lower E first, so that the direction with higher F + N comes before the faster one; (b) higher N; (c) a fixed earlier order recorded in its own column, so that the order can be checked.

## Independent second scoring

1. A second scorer scores every direction on the same three axes before seeing the first scores.
2. The second scorer reads only the gap, the data and the analysis steps of each direction, not the effort estimates.
3. Agreement is reported per axis as exact agreement and as quadratic-weighted kappa. When most scores are 2, kappa is sensitive to a few directions and is given for reference only.
4. Each difference is either adopted or kept as it was, with the reason written down. Every adopted difference goes into the adjustment register.

## Adjustment register

Every change after the freeze date is one row:

| Date | Direction | Axis | Old | New | Reason | Results seen? |
|---|---|---|---|---|---|---|

"Results seen?" records whether any result of the direction existed or had been looked at when the score changed.

## Downgrading and leaving out

- **Downgrade** a direction (keep the folder, start it only when a stated condition is met) when its core question is already covered and the remaining gap depends on scarce data, or when a hard gate such as a public phenotype inventory has not passed.
- **Leave out** a direction when a paper whose record was opened already covers it, or when public sample sizes cannot support it. List it with the covering papers in the not-kept list of the species (for grapevine, [examples/vitis/NOT_KEPT.md](../examples/vitis/NOT_KEPT.md)).
- A proposal to merge, downgrade or leave out a direction is marked [to confirm] until the maintainer decides; the frozen scores do not change until then.
