# Task board

Updated 2026-09-29. Statuses: READY, IN_PROGRESS, BLOCKED, NEEDS_REVIEW, DONE, DEFERRED. DONE requires acceptance evidence, not just code. Tasks remain BLOCKED until dependencies are DONE; the completing agent promotes newly unblocked tasks. Implementation requires the user's start instruction; a READY entry is not spending authorization.

## Current board

| ID | Task | Depends on | Status | Owner |
| --- | --- | --- | --- | --- |
| DOC-001 | Contract, pinned audit and handoff | — | DONE | Documentation session |
| BASE-001 | Upstream review and tested baseline | DOC-001 | READY | Unclaimed |
| DATA-001 | Durable project, scene and asset model | BASE-001 | BLOCKED | Unclaimed |
| COST-001 | Budget admission and paid-job recovery | DATA-001 | BLOCKED | Unclaimed |
| PLAN-001 | Brief/fact pack to editable scene plan | COST-001 | BLOCKED | Unclaimed |
| MEDIA-001 | One image and one video provider path | PLAN-001 | BLOCKED | Unclaimed |
| VIDEO-001 | Narration, subtitles, composition and export | MEDIA-001 | BLOCKED | Unclaimed |
| UI-001 | Local studio workflow and per-scene editing | VIDEO-001 | BLOCKED | Unclaimed |
| BENCH-001 | USD 10 benchmark and user-PC acceptance | UI-001 | BLOCKED | Unclaimed |
| DRAMA-001 | Character bible and short continuity pilot | BENCH-001 | DEFERRED | Unclaimed |
| TEMPLATE-001 | Evaluate Hypit and Flow interchange | BENCH-001 | DEFERRED | Unclaimed |
| SOCIAL-001 | Publishing and performance feedback | BENCH-001 + user scope | DEFERRED | Unclaimed |

Claim format: task, owner/session, branch, starting SHA, timestamp, intended files, acceptance command/artifact, remaining session budget. Store active claim in HANDOFF. Each task may be split into bounded subtasks without changing its acceptance criteria. Record splits here; do not hide unfinished criteria behind a renamed task.

## Task contracts

### DOC-001 — documentation foundation

Scope: agent contract, product, architecture, audit, tasks, validation and handoff only. Acceptance: pinned findings distinguish inspection from execution; tasks have dependencies and evidence; no application changes or API spend. Evidence: all eight contract files, documentation/link/dependency checks and the documentation PR. No application readiness is claimed.

### BASE-001 — establish the baseline

Scope: inspect local/remote branches and owner changes; compare the audited fork and upstream; propose and implement a reviewable upstream sync or bounded selection. Inspect existing generation, recovery, upload and configuration code before deciding what must be added. Keep the contract files and upstream notices.

Acceptance: recorded merge/selection rationale and resulting SHA; dependencies installed from the appropriate lockfile; required CI checks recorded; one offline/local-asset video plays; current UI launches; existing provider/upload settings are mapped; exact future extension paths documented. Automatic upload is disabled in the studio plan. Record OS/RAM/disk/FFmpeg requirements, without claiming user-PC verification. Do not absorb unrelated branches without review.

Evidence: diff/PR, command results, local sample video, UI screenshot, extension map in ARCHITECTURE. If baseline tests fail, distinguish pre-existing failures from sync regressions.

### DATA-001 — durable projects

Scope: versioned project/scene/asset/job contracts, SQLite repository, atomic asset persistence and source manifest. Start with fixture data and one project, without paid calls.

Acceptance: create/edit/reopen a project after process restart; stable scene IDs/order; reject malformed schema/path inputs; edited scene invalidates only dependent outputs; missing/corrupt assets are detected. Migration behavior is explicit. No secrets in exports.

Evidence: focused persistence/restart tests, sample sanitized project/export, documented schema.

### COST-001 — spending and recovery

Scope: transactionally reserve, reconcile and report costs for every paid stage; provider job identity and unknown-state handling; dry-run plan. Reuse audited protections where practical.

Acceptance: a concurrent reservation test cannot admit work beyond the cap; unknown price blocks submission; timeout after submission does not duplicate purchase; restart/poll/download retry reuses the existing provider job; cancellation retains unresolved reservations; actual and estimated costs remain distinct. Finite input limits and decimal accounting are enforced.

Evidence: failure-injection tests with deterministic fake provider and ledger snapshots. Tests must verify zero duplicate submissions, not merely assert an error message.

### PLAN-001 — editable editorial plan

Scope: brief + approved source pack → hook/script/scenes, character/reference hooks and platform copy. Reuse existing text-provider/social-metadata functions through the budget gate. Provide offline fixtures.

Acceptance: plans validate against duration/order/schema rules; factual statements trace to provided source facts; missing facts are visible; the owner can edit and rerun a single stage. Text-provider configuration and error paths work. No invented fixture times or teams presented as current facts.

Evidence: two preset fixture plans, focused tests, one small live text run if authorized; otherwise mark live criterion BLOCKED and checkpoint implementation.

### MEDIA-001 — generated images and motion

Scope: select one usable image path and one usable video path from upstream/provider candidates. Verify official current prices, credentials, capabilities and any Azure eligibility. Keep providers behind common capability interfaces; do not add five speculative integrations.

Acceptance: source/capability/pricing notes; fixture contract tests; bounded live image and video jobs save playable assets and provider IDs; reference input works if selected for the later continuity path; failures/resume comply with COST-001. Report unsupported capabilities honestly. A generated still plus pan/zoom does not pass live video generation.

Evidence: sanitized live request metadata, saved image and clip, measured latency and cost ledger. Missing keys/budget blocks live acceptance, not unrelated offline implementation.

### VIDEO-001 — first complete content package

Scope: reuse narration, subtitle, local rendering and music controls; assemble planned scenes and export video, image, audio, SRT, platform copy and provenance/cost manifest. Prefer a documented permissive music/font fixture.

Acceptance: both presets produce a playable 20–45 second vertical output; voice is intelligible, captions synchronized, visuals relevant and required scenes present; re-rendering accepted assets makes zero new generation calls; exports reopen correctly. Partial generation cannot be labeled complete.

Evidence: media files, ffprobe report, human watch-through notes and focused assembly tests. Compare economy mode and generated-motion mode explicitly.

### UI-001 — usable local workflow

Scope: extend the existing Streamlit interface for projects, provider settings, plan editing, estimates, progress, preview, cancel/resume and export. Keep normal setup understandable without code editing.

Acceptance: owner can complete the PRODUCT everyday flow in a browser; reopen the app and resume; regenerate one scene; see actual/reserved/unknown costs; handle missing keys and failed jobs; no accidental publication. Secrets are masked and not exported.

Evidence: end-to-end local walkthrough, screenshots, resulting media, failure/restart demonstration. A screenshot alone is insufficient.

### BENCH-001 — prove value within budget

Scope: use the owner's configured providers and explicit remaining experiment allowance; run the two benchmark briefs under the cumulative USD 10 cap, including earlier paid acceptance calls. Do not reset the ledger between tasks to manufacture a fresh allowance.

Acceptance: record every charge/unknown reservation, elapsed time, accepted/rejected outputs and regeneration count; score using VALIDATION; install and execute on the actual user PC with its OS/hardware documented. Separate local execution from user-PC evidence. If funds cannot produce both acceptable outputs, report the shortfall and measured cause; do not invent success or buy more silently.

Evidence: benchmark report, exported packages, provider reconciliation and user-PC walkthrough. Release requires subjective owner review of usefulness as well as technical checks.

### Deferred contracts

- DRAMA-001: three connected shots with the same recurring character, consistent reference/voice/wardrobe and a clear story beat; compare continuity rather than merely storing a character name. Select Huobao patterns only as needed. New paid allowance must be known.
- TEMPLATE-001: compare existing renderer against one Hypit scene using identical accepted assets; measure installation burden, render time and visual benefit; respect license boundaries. Define Flow export/import as optional manual interchange, not API autonomy.
- SOCIAL-001: choose one publishing adapter and a channel authorization process after content quality is proven. Persist post IDs and reconcile retries. Analytics begins with manual imports if useful; add OpenClaw only for proven callable tools and demonstrated coordination needs.
