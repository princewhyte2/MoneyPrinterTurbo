# Validation and evidence

Evidence must state exactly what was exercised. Use these labels in PRs and handoffs:

| Label | Meaning |
| --- | --- |
| SOURCE_INSPECTED | Specific code/manifests read at a pinned SHA |
| STATIC_CHECKED | Syntax/lint/document checks ran; no application behavior implied |
| OFFLINE_TESTED | Deterministic fixtures exercised behavior without paid services |
| LOCAL_EXECUTED | Actual app/render ran in the named development environment |
| LIVE_API_VERIFIED | Named provider/model actually returned saved, inspected output; cost recorded |
| USER_PC_VERIFIED | Named build was installed/run on the owner's actual PC |

These labels are complementary, not substitutes. A mocked provider does not become live-verified because an API key field exists. User-PC proof cannot be inferred from Linux execution in an agent workspace.

## Required evidence record

For each completed task, record task ID, commit/PR, environment, command or UI steps, expected result, observed result, exit code, artifact paths/hashes, paid cost and outstanding reservations, skipped checks and remaining limitations. Keep durable summaries in `docs/evidence/<task-id>.md` as implementation progresses. Large assets stay outside source Git; include a stable artifact location and hash. Never include credentials, signed download URLs or unnecessary personal data.

## Baseline checks

Confirm these against the resulting revision after BASE-001; they describe the audited fork's CI approach:

```bash
uv sync --frozen --python 3.11
uv run --no-sync python -m compileall app cli.py main.py webui test
uv run --no-sync ruff check app cli.py main.py webui test
uv run --no-sync python -X utf8 -m coverage run -m pytest -q test
uv run --no-sync python -m coverage report
```

Existing CI also includes Python 3.13 and Windows smoke coverage. Do not quietly weaken required CI gates. Live tests are disabled by default; `MPT_RUN_INTEGRATION_TESTS=1` can invoke external services and must not be set as a routine test shortcut. Run focused tests during development and the required gate for the milestone, not every expensive check after every small edit.

## Release scenarios

1. **Economy explainer:** approved local/owned stills or clips, generated script and voice, subtitles and platform copy. Clearly identify image animation versus generative motion.
2. **Match-preview trailer:** fictional/source-backed fixture, hook, at least one actual generated motion shot, narration, captions, permitted music and cover. No fabricated current sports claims.
3. **Failure recovery:** interrupt after provider submission and after asset download; resume without duplicate purchase. Restart before compose and reuse assets. Verify cancellation and unknown-cost display.
4. **Budget boundary:** concurrent reservations, unknown pricing, too-long duration and insufficient remaining funds cannot trigger unbudgeted new work.
5. **Portability:** clean setup on the actual user PC, keys entered locally, end-to-end export, then reopen the saved project.

## Technical checks

- Target 1080×1920, 20–45 seconds; report actual dimensions, frame rate, audio codec and duration with ffprobe. Any deliberate deviation is visible.
- Play the entire video: no black gaps, corrupt frames, accidental freezes, cut-off speech, clipped captions or overpowering music. Use allowed platform-safe margins checked in the preview.
- Confirm scene count/order, subtitle timing, intelligible speech, exports and manifests. The presence of an MP4 file is not enough.
- Confirm that re-rendering with unchanged assets issues no new paid requests and that a missing required scene prevents a success status.

## Editorial scorecard

Human score each item from 1 (unusable) to 5 (strong): opening hook, visual relevance, pacing/scene variety, narration/audio, caption readability, brand/story coherence. For drama add character/voice continuity. Proposed acceptance: at least 4 on each applicable item, plus owner approval of the final sample. Do not replace human review with a fabricated model quality score. If the threshold is not met, record specific weaknesses and targeted revisions.

## USD 10 experiment report

Record cumulative spend for scripting, images, video, TTS and retries, plus outstanding/unknown charges. Separately record coding-agent usage if known; never estimate it as measured usage. Report cost per attempted output and per accepted output, total elapsed time, hands-on time, rejected shots and reuse savings. Any earlier live adapter tests count against this same experiment unless the owner explicitly allocates a separate budget.

No fixed video count is promised. Provider invoicing can differ from estimates; state unresolved amounts and use available provider-side limits. Stop new submissions when remaining funds cannot safely cover them.
