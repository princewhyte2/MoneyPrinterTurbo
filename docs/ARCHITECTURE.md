# Architecture and decisions

Status: proposed implementation contract, grounded in the static audit dated 2026-09-29. Nothing in this file implies that the planned studio layer has already been built.

## Foundation decisions

| Decision | Reason | Revisit when |
| --- | --- | --- |
| Extend the Python MoneyPrinterTurbo fork | Existing UI, API, CLI, narration, subtitles and rendering | A documented prototype demonstrates an unavoidable limitation |
| Review upstream before writing adapters | Audited fork main is 316 commits behind; upstream adds generation integrations | Upstream review identifies incompatible changes |
| Keep Streamlit for the initial UI | Avoid an extra frontend/build/deployment stack | Actual UX requirements cannot be satisfied |
| Add a small studio layer with durable local state | Scene identity, cost reservation and recovery must outlive process memory | Scale creates a demonstrated need for a service database |
| Prefer SQLite plus local asset files | Transactional reservations and simple PC installation | Concurrent remote users are explicitly in scope |
| Use Huobao as a selective MIT reference | Strong story/scene data structures without importing an entire web app | A bounded reuse candidate is identified |
| Keep Hypit external and optional | Different runtime and modified license | A benchmark justifies the adapter and distribution terms are resolved |

Do not delete existing functionality simply because it is out of the first release. Isolate or disable automatic uploading in the new export-only workflow. Preserve source notices for code actually reused.

## Logical flow

Brief + fact pack → script/scene plan → budgeted asset jobs → narration/subtitles → composition → preview/export.

The studio orchestrator calls existing MPT services through small adapters where practical. The first implementation task must map upstream provider behavior before choosing extension points. Avoid concurrent mutation of global provider configuration; use request-scoped configuration or serialize calls until refactored safely.

Suggested boundaries, with exact paths finalized in BASE-001: `app/services/studio/` for orchestration, provider interfaces, storage and budget; `app/models/` for validated contracts; existing `webui/` for UI. Keep the renderer separate from paid generation so local re-renders do not buy new assets.

## Persisted contracts

| Record | Required contents |
| --- | --- |
| Project | ID, schema version, brief, preset, source facts/URLs/dates, aspect, duration, style, budget, currency |
| Scene | Stable ID/order, script/dialogue, duration, visual prompt, asset mode, character/reference IDs, voice ID, revision |
| Asset | ID, content hash, local path, type, provider/model/version where supplied, prompt/reference hashes, source and rights note |
| Job | ID, scene/stage, input hash, state, provider request ID, timestamps, output IDs, sanitized error |
| Cost entry | Job ID, units/rate/source/date, estimated upper bound, reserved amount, reconciled amount or explicit unknown status |
| Export | Video/cover/audio/SRT/copy paths, source plan, asset manifest, measured technical checks and cost report |

Store secrets outside these records. A project export must be portable and must not expose API keys or reusable signed URLs. Version schemas; test migration of saved projects before changing them.

Job states: planned → reserved → submitted → running → succeeded/failed/cancelled; use `unknown_remote_state` whenever submission may have succeeded without confirmation. Persist checkpoints before advancing. Cancellation prevents new submissions; it cannot assume a remote job was cancelled or refunded.

## Budget and recovery invariants

1. Account for all paid stages, including scripting and TTS, not just video. Verify current model pricing from the provider before selecting live defaults; store currency, units and verification date. No invented universal per-video price.
2. Before submission, atomically reserve a conservative maximum charge. Permit a job only if reconciled spend + unresolved reservations + new reservation remains within the configured cap. Use decimal amounts or integer subunits.
3. Unknown pricing or an unbounded charge blocks automatic paid submission. Apply token/duration/resolution limits. Provider-side prepaid limits are an additional guard where available; local accounting cannot guarantee a provider's invoice.
4. Record an idempotency key when supported and persist provider job IDs immediately. A timeout after submission is not proof of failure: poll/reconcile the same job, do not submit a replacement blindly.
5. Download failures retry retrieval of the existing output. Retry generation only after definitive failure and a fresh budget check. Keep unresolved reservations until a charge is known or safely reconciled.
6. Use content hashes over model/settings/prompt/reference inputs for reuse. Accept a cached asset only if it exists and validates. Scene edits invalidate their affected outputs and composition, not unrelated scenes.
7. Persist database updates transactionally and files atomically. On restart, reconcile interrupted work and validate outputs. Reopening a project must not silently call a paid API.

Initial scheduling is serial paid submission with bounded polling. Parallel generation can be added after reservation races and unknown-state recovery are tested. Do not rely on Huobao's usage counter as a hard cap: the audited `checkBudget` does not reserve the estimated next charge.

## Providers and export

Define capability contracts for text, image, image-to-video/text-to-video and TTS: validate configuration, estimate maximum cost, submit, poll when applicable, retrieve and normalize errors. Expose supported sizes/durations/reference images rather than assuming all endpoints are interchangeable. OpenAI-compatible text/image endpoints do not imply video protocol compatibility.

Start with the lowest-cost suitable configured provider, not a provider chosen solely because its name appears in a README. Reuse upstream paid-request recovery protections. Optional Azure use requires a verified eligible deployment; credits are not portable across unrelated providers.

Proposed export layout: `exports/<project>/<run>/final.mp4`, `cover.png`, `voice.wav`, `captions.srt`, `copy.json`, `project.json`, `manifest.json`, `costs.json`, plus relative asset paths. Format conversion must preserve a separate original asset. Keep output files outside Git.

## Changes to decisions

For a material change, append date, evidence, alternatives, decision and affected task IDs here. User suggestions add to the candidate set; do not erase previous findings. Reject a component when it duplicates a working capability, increases operational burden without benefit, or has unresolved reuse terms.
