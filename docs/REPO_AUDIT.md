# Repository audit

Audit date: 2026-09-29. Evidence: pinned Git source, manifests, licenses and selected implementation paths. No dependency installation, application startup, provider call, render benchmark or user-PC test was performed in this audit. Demos and README claims are not treated as runtime proof. This is a scoped implementation/reuse review, not a complete security or legal review.

## Comparison and decision

| Repository and pinned revision | Observed strengths | Observed limitation | Decision |
| --- | --- | --- | --- |
| [User MoneyPrinterTurbo fork](https://github.com/princewhyte2/MoneyPrinterTurbo/tree/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb) | Python, Streamlit, FastAPI, CLI, narration, subtitles, rendering and task artifacts | Audited main is behind upstream; full studio recovery/budget not demonstrated | Foundation |
| [Upstream MoneyPrinterTurbo](https://github.com/harry0703/MoneyPrinterTurbo/tree/d47783266cfad72663c8bf84b59694a9034450b0) | Additional AI images/video integrations and paid-request recovery handling | Large change set requiring baseline tests; still not proof of our scene workflow | Review/sync before adding duplicate features |
| [Huobao Drama AI, dav-niu474 variant](https://github.com/dav-niu474/huobao-drama-ai/tree/eece93fa0d2cb3b72551f80a1aa63b9d1d6111d6) | Drama/episode/character/storyboard data, staged pipeline, composition, usage tracking | Full Next/Prisma app; in-memory batch state; budget check is not a reservation | Selective MIT patterns/code with attribution |
| [Hypit](https://github.com/hypit-ai/hypit/tree/b00532e413d83845b631df25f2319017541db0ac) | Authored video workflow, plan/build/result operations, explicit asset reuse | Additional runtime; modified Apache terms; no implicit cache | Optional external adapter after a measured benefit |
| [MicroDrama AI](https://github.com/Anil-matcha/Open-AI-Micro-Drama-Generator/tree/94ef2a6611696f353a8fc319fbef81b248725e20) | Compact idea→script→storyboard→frames→video example | MuAPI coupling; missing LICENSE despite MIT badge; failures can omit scenes | Reference only; no source copying until license clarified |

Exact repository identity matters: the inspected Huobao is the `dav-niu474` variant. Findings and its license must not be attributed to every similarly named Huobao project.

## MoneyPrinterTurbo: keep and extend

The fork's audited `main` is **0 commits ahead and 316 behind** the pinned upstream main, according to the GitHub comparison. The pinned diff spans 150 files, about 44,533 added and 1,894 removed lines. This describes these branch tips only; it does not rule out work on other branches or the owner's PC. Recheck before syncing.

Source anchors at the fork revision:

- [pyproject.toml](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/pyproject.toml): project 1.3.3, Python >=3.11, existing dependency/lockfile approach.
- [task.py](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/app/services/task.py), [llm.py](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/app/services/llm.py), [video.py](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/app/services/video.py): existing script, terms, audio, subtitle, composition and social-metadata functions. Wrap existing capabilities rather than replacing them wholesale.
- [state.py](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/app/services/state.py): in-process MemoryState by default, optional Redis. This is not evidence of complete durable local scene recovery.
- [task_artifacts.py](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/app/services/task_artifacts.py): atomic script JSON updates, useful persistence primitive.
- [LICENSE](https://github.com/princewhyte2/MoneyPrinterTurbo/blob/e5bb283d2f3cec00ac9b32c306b0387fbedfb9cb/LICENSE): MIT. Bundled media needs a separate rights inventory; the music README's provenance statement is not a blanket asset license.

Upstream [material.py](https://github.com/harry0703/MoneyPrinterTurbo/blob/d47783266cfad72663c8bf84b59694a9034450b0/app/services/material.py) includes OpenAI-compatible image generation, WaveSpeed video generation and on-demand video paths. Provider modules include `volcengine_seedance.py`, `muapi.py`, `loomloom.py`, `ofox.py` and `metaso_minimax.py`. Their presence is evidence of code, not verified account access or output quality.

Important existing protections: ambiguous paid image submissions stop instead of blindly retrying; some paid video paths retain request IDs and stop on uncertain state/download failures. Preserve these protections. They do not establish a cross-provider USD budget ledger. Upstream also has cross-post recovery: do not confuse publishing recovery with full scene-generation resume.

Action: BASE-001 reviews upstream changes in a dedicated branch, checks for owner changes, records a decision to sync all or selected commits, and runs the baseline. Do not blindly merge the 316 commits as part of the documentation task.

## Huobao: story structure, not a second application

At the pinned revision, [prisma/schema.prisma](https://github.com/dav-niu474/huobao-drama-ai/blob/eece93fa0d2cb3b72551f80a1aa63b9d1d6111d6/prisma/schema.prisma) defines drama, episodes, characters, storyboards, scene images, generation costs and budgets. [batch-pipeline.ts](https://github.com/dav-niu474/huobao-drama-ai/blob/eece93fa0d2cb3b72551f80a1aa63b9d1d6111d6/src/lib/batch-pipeline.ts) structures script, extraction, voice, storyboard, image, video and composition stages, but stores batch runtime state in in-memory maps.

The episode composition route `src/app/api/episodes/[id]/compose/route.ts` includes FFmpeg composition and browser fallback instructions. [usage-tracker.ts](https://github.com/dav-niu474/huobao-drama-ai/blob/eece93fa0d2cb3b72551f80a1aa63b9d1d6111d6/src/lib/usage-tracker.ts) checks current usage and records usage afterwards; the inspected check does not reserve `estimatedCredits`. It is not sufficient for our strict admission budget under concurrency.

[LICENSE](https://github.com/dav-niu474/huobao-drama-ai/blob/eece93fa0d2cb3b72551f80a1aa63b9d1d6111d6/LICENSE) is MIT. Reuse only bounded pieces whose dependencies and notice obligations are documented. Defer its auth, marketplace, collaboration and publishing machinery. Character-reference data alone does not prove visual consistency; test repeated shots.

## Hypit: optional composition backend

The inspected [run documentation](https://github.com/hypit-ai/hypit/blob/b00532e413d83845b631df25f2319017541db0ac/docs/quickstart/run.md) and CLI/runtime source describe author/run files, runtime initialization, plan/build/get and explicit build-result reuse. The actual lifecycle includes `hypit runtime init`, `hypit runtime use hypit.runtime.json`, `hypit runtime up`, and plan/build/get operations; confirm exact arguments from the pinned CLI before scripting an adapter. Do not invent a generic `hypit render script.json` interface.

Reuse is explicit through prior build outputs and satisfaction edges; documentation says there is no implicit cache. The adapter must map accepted assets deliberately to avoid paying for new generations. Extra runtime/browser dependencies must justify their installation burden.

The [LICENSE](https://github.com/hypit-ai/hypit/blob/b00532e413d83845b631df25f2319017541db0ac/LICENSE) is modified Apache, with conditions on third-party hosted functionality, commercial redistribution and notices. It expressly describes internal organizational/client work and output ownership. Treat these as source terms to review for the chosen deployment, not permission to copy/relicense Hypit into an MIT package. External installation does not automatically resolve every distribution question. Phase A does not depend on Hypit.

## MicroDrama: useful sequence, unresolved copying permission

[idea2video.py](https://github.com/Anil-matcha/Open-AI-Micro-Drama-Generator/blob/94ef2a6611696f353a8fc319fbef81b248725e20/server/pipelines/idea2video.py) develops a story, extracts characters, writes scenes, generates scene videos and concatenates them. [script2video.py](https://github.com/Anil-matcha/Open-AI-Micro-Drama-Generator/blob/94ef2a6611696f353a8fc319fbef81b248725e20/server/pipelines/script2video.py) generates portraits, storyboards, first frames and clips. It can regenerate portraits per scene and use the first matching character portrait; this does not establish multi-character continuity. Exceptions can drop shots/scenes and still produce a final video.

Useful lesson: preserve story→scene→shot separation. Do not copy its silent partial-success behavior: our exports must report missing required scenes and cannot pass release acceptance until resolved.

The README has an MIT badge, but no tracked LICENSE file was found in the pinned tree. Clarify terms before copying. No implementation depends on this repository.

## What remains unproven

Cold installation, actual model access, quality, latency, total cost, Windows behavior, browser UX and restart behavior require execution. The audit does not rank model prices or promise a video yield for USD 10. Verify current official provider pricing during provider selection, then measure actual accepted outputs. No new repository search is needed unless a concrete missing capability emerges.
