# Current handoff

Updated: 2026-09-29. Milestone: documentation foundation only.

## Current state

- Repository: `princewhyte2/MoneyPrinterTurbo`.
- Documentation branch: `docs/local-studio-agent-contract`.
- Audited starting main: `e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb`.
- Audited upstream main: `d47783266cfad72663c8bf84b59694a9034450b0`.
- DOC-001 complete: agent contract, product, architecture, pinned audit, task board, validation and startup prompt.
- Implementation has not started. No dependencies installed for the audit, no application tests/run, no paid generation, no generated sample media, no upstream merge and no user-PC test.
- Foundation decision: keep the Python fork and existing UI; review upstream additions before extending. Huobao selective reference, Hypit optional external adapter, MicroDrama reference-only pending license clarification.

## Next task

**BASE-001**, once the user requests implementation. Start from the branch/commit containing this contract, inspect working tree and branches, then review upstream changes. Produce a tested baseline and the extension map. Do not start a new app, re-audit all repositories, or buy media during this task.

First commands are in START_HERE. Read REPO_AUDIT's MoneyPrinterTurbo section, then inspect relevant provider, task, state and UI changes at the pinned revisions. Recheck current branch divergence before choosing a sync strategy. Main may advance after this audit; never assume the recorded SHA is still the tip.

Active implementation owner: none. No implementation claim is held by this documentation session. On claiming BASE-001, record session/owner, branch, HEAD, timestamp, intended files and next acceptance check here.

## Environment and preserved unrelated work

The audit used a Linux agent workspace with Python 3.12.14, Node 24.19.0, git 2.51.1 and `/usr/bin/ffmpeg`. This is not the owner's PC. Use the project's tested Python versions rather than assuming the audit interpreter is the desired runtime.

In this session's clone, an unrelated untracked file existed at `resource/fonts/.STHeitiMedium.ttc.S87Qjd`. It was not added, modified or deleted. Preserve unrelated files in any continuing checkout; a fresh clone need not contain this file. Do not interpret it as application work.

## Inputs still needed at the relevant task

- BASE-001/BENCH-001: actual PC OS/hardware and installation environment. Most source work can proceed before this is known; user-PC verification cannot.
- PLAN-001/MEDIA-001: locally configured usable API keys, selected provider/model, dated official pricing and applicable spending authorization. Never request secrets in a repository issue or chat transcript.
- BENCH-001: approved brief/assets and remaining cumulative media allowance. Initial intent is USD 10, not unlimited retries.

## Checks for this documentation change

Source inspection only for applications. Before publishing the documentation PR, check whitespace, local Markdown links, task dependency references and the exact staged file list. No full application suite is required for this documentation-only change. Final check results are recorded in the PR body; do not infer app readiness from them.

## Future handoff template

Replace current-state sections as work advances and retain material decisions in ARCHITECTURE:

```text
Task / status / owner:
Branch and starting SHA:
Latest checkpoint SHA / PR:
Goal and changed paths:
Verified commands and observed results:
Evidence/artifact locations and hashes:
Live provider/cost/reservations (or none):
Known failures, reproduction and skipped checks:
Dirty/unrelated paths to preserve:
Exact next action and acceptance check:
Required user input, only if blocking:
```

If interrupted, an honest incomplete checkpoint is useful. A fabricated DONE status is not.
