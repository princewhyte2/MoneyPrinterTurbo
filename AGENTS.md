# White Array agent contract

This file governs work on White Array's local content studio in this fork. It is a project contract, not a claim that the planned features exist. Read `docs/START_HERE.md`, `docs/PRODUCT.md`, `docs/HANDOFF.md`, and the selected entry in `docs/TASKS.md` before editing. Read architecture and evidence requirements for implementation work; read only the relevant audit entries when evaluating dependencies.

## Scope and authority

- Build a PC-first studio for short videos, images, narration, subtitles and social copy. Manual upload first. Story/drama capabilities follow the first working short-video release.
- Extend this MoneyPrinterTurbo fork. Review upstream improvements before duplicating them. Do not rewrite the application in TypeScript or merge several complete applications together.
- New user instructions take precedence. Preserve earlier compatible decisions. Record a changed decision, its reason and affected tasks; do not silently replace the product direction.
- Current authorization covers this documentation/audit foundation. These instructions are not permission for future spending, publishing or deployment. Implementation starts when requested.

## Working protocol

1. Inspect branch, HEAD, `git status --short`, existing instructions and handoff. Preserve unrelated user changes. Never force-reset or use broad staging when unrelated files exist.
2. Select one READY task whose dependencies are DONE. Record owner/session, branch, starting SHA, scope and status IN_PROGRESS before changing code. If another owner is active, coordinate; do not assume inactivity from elapsed time alone.
3. Work in a task branch or isolated worktree. One builder owns shared pipeline/schema files at a time. Parallel work is optional and needs explicit delegation with disjoint paths and contracts; it does not inherently reduce credits.
4. Reuse existing implementation. Pin borrowed code to a revision, record its origin, preserve required notices, and check the actual license. A README badge is not sufficient permission.
5. Implement the smallest end-to-end change satisfying the task. No unrelated refactors, speculative providers or repeated whole-repository research.
6. Run focused checks for changed behavior and the required CI gate. Record command, environment, result, skipped checks and artifact paths. Do not equate mocks with a live service or a screenshot with a playable video.
7. Commit a coherent checkpoint and update TASKS, HANDOFF and evidence together. Open a reviewable PR when appropriate; do not merge merely to finish a task.

## Cost, credentials and safety of execution

- Default to offline fixtures/dry runs. Never enable live integration tests implicitly. Reuse applicable user spending authorization; otherwise obtain a concrete provider/budget authorization before paid calls.
- The intended media experiment is capped at USD 10; coding-agent credits are a separate budget. Do not assume Azure credits cover arbitrary APIs or third-party model charges.
- Before paid generation, enforce the budget ledger described in ARCHITECTURE, including outstanding reservations and ambiguous requests. Do not retry a paid submission blindly.
- Keys stay in local ignored configuration/environment, never Git, prompts, reports or logs. Sanitize provider errors and signed URLs. Keep network services local by default.
- Keep automatic publishing disabled in this phase, including existing upload hooks. No public posts, account setup or cloud deployment as a side effect of rendering.

## Definition of done and stopping

- A task is DONE only when its acceptance criteria have evidence. Use BLOCKED for missing inputs and NEEDS_REVIEW for unresolved review; never fabricate a passing result.
- Completion of a provider adapter requires both contract tests and a separately labeled live proof when credentials and budget are available. An implementation may be checkpointed without claiming live readiness.
- Use `docs/VALIDATION.md` for quality and recovery gates. State what is source-inspected, locally executed, live-provider verified and verified on the user's PC.
- At the agreed time/token boundary, checkpoint instead of starting another subsystem. Leave exact next action, unresolved failure and reproduction command. If unable to commit, list all dirty paths and attach a recoverable patch.
- Update this contract only for actual policy changes. Routine task progress belongs in TASKS/HANDOFF.
