# Evidence log template

One log per project, kept in the project folder as `EVIDENCE_LOG.md`. Add entries at the end only. Never edit or delete an old entry; fix a mistake with a new entry that points to the old one.

## Entry

```
### Entry NNN - YYYY-MM-DD HH:MM (UTC+8)

- Step: what was done, in one or two lines.
- Tool and version, and the exact command or script name.
- Inputs: file names with sha256 (or the manifest name and its sha256).
- Outputs: run folder and files, with sha256; status .DONE or .FAILED.
- Source read: DOI or URL you opened, and the date you opened it. Write [to confirm] if you did not open it.
- Post-hoc: yes or no. If yes, say what was changed after which result was visible.
- Notes: anything that surprised you, and what you will do next.
```

## Rules

- Write the entry when the step is done, not later.
- Record failures and dead ends as entries too.
- A number in a paper or table must trace back to an entry.
- Do not put private data, sample details, host names or local paths in the log.
