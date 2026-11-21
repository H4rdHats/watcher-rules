# watcher-rules

This repository holds the watcher-rules file and its PIN for the HardHats Claude Code cloud routines.

It contains only:

- `watcher-rules.txt` — the in-force rules (LF-only)
- `PIN.sha256` — one line: `sha256 size version` of that rules file
- this `README.md`

Do not add history packets, yes records, loader text, or anything private.

## Read

The files on `main` are public so the routines can fetch them over HTTPS from `raw.githubusercontent.com`, using the `main` ref only. A short frozen loader in each routine checks the fetched bytes against `PIN.sha256` before it follows the rules.

## Write

Only the owner `H4rdHats` may write; there are no collaborators. The Claude GitHub app and any cloud builder must not be installed here. Never Claude Code. `main` is protected by two rulesets: Ruleset A blocks force-pushes and deletions and has no bypass; Ruleset B requires a pull request, and its only bypass is the Repository admin role (the owner).

A rules update is: Engineering freeze → Security and Reviewer POST on the exact sha → Ashley's typed yes naming that sha → the owner `H4rdHats` makes one direct commit of `watcher-rules.txt` and `PIN.sha256` to `main` via the Repository admin bypass on Ruleset B → Security and Reviewer spot-check that the PIN equals the yes record. The routine loader texts stay unchanged.

## PIN format

`PIN.sha256` is one LF-terminated line, three fields separated by a single space:

```
<sha256> <size-in-bytes> <version>
```

The sha256 is 64 lowercase hex characters only, and is of `watcher-rules.txt`. The size is the byte count of that file. The version must match the line-1 header token of that file (`WATCHER / CLOUD ROUTINE RULES <version> …`), not an adoption name.
