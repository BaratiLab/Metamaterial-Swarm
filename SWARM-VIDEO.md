# A Metamaterial Agentic Swarm — explanatory movie

**A Metamaterial Agentic Swarm: Coordinated Search for Discrete Mechanical Design**
(implementation name: Clockwork)

| File | What it is |
|---|---|
| `metamaterial_swarm.mp4` | Full film, 59.5 s, 1920×1080, 30 fps, H.264, silent |
| `metamaterial_swarm_preview.gif` / `.webm` | Compact looping preview for the README (recorded replay and endpoint, 21 s) |
| `metamaterial_swarm_poster.png`, `metamaterial_swarm_thumbnail.png` | Poster frame (1920 px) and thumbnail (1280 px) |
| `index.html` | Editable source and interactive demo: play/pause, speed, time scrubber, and a slider to inspect any of the 961 recorded events |

Open `index.html` in a browser. It reads `data/seed0_events.js`, the role icons in `assets/` and the fonts in `fonts/` by relative path.

## What is recorded and what is illustrative

The film labels every moment with an on-screen badge and a caption tag: **ILLUSTRATIVE** (amber, dashed) or **RECORDED** (teal, solid).

**Recorded data** (from `data/seed0_events.json`, seed 0):
- the evaluation counter, 1 to 961 charged evaluations; cache hits count toward the budget
- the proposing agent highlighted in the replay (A1–A40, I1–I5), its declared specialty and the action it actually executed
- each candidate loss, the unresolved flag (no finite loss; the previous incumbent is kept and drawn as a red tick, never as a high score), the cache flag, and the monotone best-so-far curve
- the archive cards' losses and evaluation numbers: the lowest distinct resolved losses recorded so far, deduplicated by label hash
- the loss shown for A3, A12, A21 and A40 inside the explanatory scenes: each is that agent's first recorded query (evaluations 4, 13, 22, 41)
- the endpoint geometries (`assets/swarm_designs.png`) and the strict endpoint losses: 0.100590, 0.139274, 0.135858; mean 0.125241. Only seed 0 falls below 0.1102 (first at evaluation 832)

**Illustrative mechanics** (schematic, not a replay):
- parent tiles, proposal tiles and archive mini-tiles. Each tile is a 4×4 schematic; archive and replay tiles are derived from the label hash only so that different designs look different
- the parent splitting into five islands, read/propose/send/return arrows, acceptance outcomes, the learner histogram, the recombiner's donor (I2) and the polisher's single-cell change
- the logs do not record archive reads, donor identities or per-iteration parent snapshots, so the film does not claim an exact donor or parent replay or a winning lineage

## Evidence boundaries kept in the film
- The 40 agents are numerical search policies, not language models: 5 islands × the same 8 specialties, with separate parents and random streams.
- Physical solves are serial. One proposal reaches the single evaluator at a time, and the replay never shows concurrent solves or all-to-all messaging.
- The evaluator is the full-resolution source-Q4 zero-void Schur-limit model. The film shows no experimental validation, no finite-void physics and no FEA fields.
- It makes no claim of superiority over coordinate search and no claim of a causal benefit from communication. The beam pilot is not included.
- Search-loop best-so-far (0.10058956168) and the strict endpoint re-evaluation (0.10058956170) agree to solver precision.

## Rebuilding the film
The film is a deterministic HTML composition. `window.drawFrame(t)` draws the frame for time `t` with no live animation state.
1. `python3 tools/build_data.py data/seed0_events.json data/seed0_events.js` regenerates the embedded data and asserts its integrity.
2. `node tools/render.js index.html s1.mp4 0 375`, and likewise for frames 375–720, 720–1065 and 1065–1785. This needs Playwright with Chromium and ffmpeg.
3. Concatenate the four files with `ffmpeg -f concat -c copy`.
4. `node tools/validate.js index.html data/seed0_events.json` re-checks the counter, the curve against the JSON, the dot and unresolved counts, the 40/8/5 structure, and text and arrow clipping.

Note: the request named a "HyperFrames" animation skill, but no skill by that name was installed in the build environment. The film was built with the same approach (seekable HTML composition, rendered frame by frame with headless Chromium and ffmpeg), without HyperFrames itself.
