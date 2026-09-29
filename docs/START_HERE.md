# Start or resume the White Array studio

Date: 2026-09-29. Repository: https://github.com/princewhyte2/MoneyPrinterTurbo

The durable memory is this repository and its commits, not an agent's chat history. An agent must have the branch containing these files. Until the documentation PR is merged, checking out `main` alone will not load this contract.

## Universal agent prompt

> Continue White Array's local content studio in this repository. Read AGENTS.md, docs/PRODUCT.md, docs/HANDOFF.md and docs/TASKS.md. Inspect the current branch, HEAD and working tree before editing. Take the next READY task with satisfied dependencies; read its relevant architecture, audit and validation sections. Preserve compatible decisions and unrelated work. Implement only that task, verify its acceptance criteria, and commit a reviewable checkpoint with TASKS and HANDOFF updated. Distinguish mocked, locally executed, live-provider and user-PC evidence. Do not spend on APIs or publish content without applicable authorization. Finish with the commit/PR, verified results, remaining limitations and the exact next task.

For the first implementation session, append: **Start BASE-001. Review the pinned upstream changes and establish a tested baseline. Do not make paid API calls.**

## Files and their jobs

| File | What the next agent learns |
| --- | --- |
| [PRODUCT.md](PRODUCT.md) | Goal, first release, later phases and user workflow |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Foundation, data contracts, budget and recovery rules |
| [REPO_AUDIT.md](REPO_AUDIT.md) | Pinned source findings, reuse decisions and limitations |
| [TASKS.md](TASKS.md) | Dependency order, scope, acceptance and ownership |
| [VALIDATION.md](VALIDATION.md) | Evidence levels and release acceptance |
| [HANDOFF.md](HANDOFF.md) | Current state, blockers and next action |

## One session, one useful checkpoint

1. Load the four startup files and relevant task context, not every old conversation.
2. Claim a bounded task; state the intended result and a session limit (suggested 45–60 minutes, not a required wait).
3. Implement and run focused checks. Stop expansion when the acceptance criteria are met.
4. Record evidence and a commit. If incomplete, leave an honest checkpoint with remaining work.
5. Review milestones: upstream baseline, budget/recovery, first playable short, first paid benchmark and first drama sequence.

A separate reviewer can work from the PR diff and evidence. Repeatedly asking several agents to read the whole project wastes credits. Different agents cannot be guaranteed identical judgment; explicit fixtures, acceptance criteria and recorded decisions keep their work comparable.

## First commands

```bash
git status --short
git branch --show-current
git rev-parse HEAD
git log -5 --oneline
```

Do not install or invoke an unrelated tool stack just to resume. If the task branch is unavailable, obtain the documentation PR/branch instead of inventing the missing state.
