# Product contract — White Array Content Studio

Version 1, 2026-09-29. This contract captures the latest local-first direction and supersedes earlier suggestions that required OpenClaw, n8n, a new TypeScript application or cloud deployment before producing content.

## Outcome

The owner opens a local browser interface on their PC, enters a brief and approved facts/assets, chooses configured providers and a budget, then gets a coherent content package. The application performs generation and assembly; the owner can upload the results manually. API keys are supplied locally. Success means useful, playable output and visible cost, not merely connected APIs.

The first paid experiment has an intended USD 10 ceiling. The number of acceptable outputs is a measured result, not a promise. Coding-assistant subscriptions, API generation, local electricity and cloud charges are separate costs.

## First release: short-video content package

- Two presets: a football match-preview trailer and an evergreen football explainer. Use fictional/sample fixtures for offline testing; obtain current, sourced match information for real previews.
- A 20–45 second vertical video, targeting 1080×1920, with an immediate hook, deliberate scenes, narration, readable subtitles, appropriate music and a clear ending.
- A generated image/cover, an editable script and scene plan, separate audio and SRT, and copy tailored for TikTok, Facebook and LinkedIn.
- An economy mode using owned/approved assets and animated stills, plus a mode with API-generated images and at least one real generated motion shot. Clearly label the mode; a slideshow does not prove video-model integration.
- A preview/edit step, optional bounded auto-run, per-scene regeneration, cancellation, resume and an export folder containing the assets and cost/provenance manifest.
- One working provider per required capability first, selected from the owner's available credentials and verified pricing. Support replaceable adapters, not every provider on day one.

Manual export is the initial delivery path. Google Flow prompt/asset export and importing the resulting clips are useful optional fallbacks; manual Flow work does not count as proof of autonomous video generation.

## The everyday flow

1. Open the studio and select a preset, brief, target duration, style and budget.
2. Provide a source pack (fixture date, teams, facts and permitted assets) or use a sample pack. Review extracted facts; the app must not invent live match details.
3. Generate the hook, script and scene plan. Show asset choices, provider capability checks and a dated cost estimate.
4. Start a bounded run. Generate required stills/clips/voice, reuse accepted assets, assemble subtitles, music and video, and show progress and reserved/spent amounts.
5. Watch the result. Replace or regenerate only weak scenes. Changes invalidate only affected downstream assets.
6. Export video, cover, captions, source files and a run report. Upload manually.

## Later phases, preserved rather than forgotten

| Phase | Outcome | Entry condition |
| --- | --- | --- |
| A | Local short-video studio and USD 10 benchmark | Current implementation target |
| B | Short drama: character bible, reference images, stable voices, shot continuity and episodes | First short-video release passes validation |
| C | Reusable premium motion/layout templates; optional Hypit adapter; Flow interchange | Measured benefit over the existing renderer |
| D | Publishing adapters, schedules, channel authorization and analytics import | User requests publishing; content quality is established |
| E | Research scheduling, daily summaries and performance-guided experiments; optional OpenClaw | Existing tools work reliably as callable code |

OpenClaw is an optional coordinator of proven tools, not a dependency of rendering. n8n is unnecessary for the first release. Postiz or another posting engine remains a later integration candidate. No automatic engagement spam or unsupported promise of business growth.

## Explicit limits and open inputs

No multi-tenant SaaS, autonomous social posting, 24/7 hosting, local GPU training, full-length series or exhaustive provider catalog in phase A. API models can run remotely while editing/rendering runs locally; a powerful local GPU is not assumed.

The owner's PC OS, RAM, available disk space, installed FFmpeg and preferred provider/model keys remain unverified. Prioritize a Windows-friendly path but verify the actual machine before calling it PC-ready. Do not assume Azure startup credits are usable for a chosen model; verify the subscription, region, quota and billing eligibility when selecting it.

Team names and fixture facts are inputs; broadcast clips, music, badges, fonts and likeness assets need recorded usage rights. Do not infer asset rights from a repository's code license. For benchmarks, use fictional teams and owned/permitted media unless real assets are confirmed.
