# Build guide

Build in this order. Finish and **test each stage with real data** before starting the next: a problem
found at stage 3 is cheap; the same problem found in a finished video takes hours to trace.

## 0. Write it down

- Fill in `decisions.md` (from `templates/`).
- Turn it into `flow.md` (from `templates/`): the exact spec of one video and of each stage. When the
  design changes, change `flow.md` first.
- Make one video **by hand** first (any editor) to prove the format is worth automating.

## 1. Repo and stack

- Git repo with a `.gitignore` that excludes `.env` and data folders **before** the first commit.
- `compose.yaml` with every service; `.env` with generated random secrets.
- Start it, open each tool's page, confirm each answers. Write the addresses in your README.

## 2. Script intake

- A place to put scripts in (a form, a folder, a sheet) and a validator: required fields, word counts,
  scene count. Bad input gets a readable error.
- The queue: one row per video with a status.
- Test: a good script queues; a broken one is refused with a clear message; a duplicate is refused.

## 3. Voice

- Speech per sentence or scene, saved as files, with durations (or word timestamps).
- Test: durations measured by your code match what a tool like `ffprobe` reports.

## 4. Visuals

- Search, licence check, filters, verified download, fallback pool.
- Test on 20 real scenes. Count: exact matches, wrong matches, fallbacks. Fix the rules, re-test.

## 5. Render and captions

- Compose images/clips to the voice timings, captions on top, logo in the safe zone.
- Test: watch it on a phone. Check timing at the start, middle and end, and the file's duration and size.

## 6. Upload

- Start with **private** or draft uploads only. Titles, descriptions, credits, tags, playlist.
- Test: one upload; check it in the platform's studio app (recognized as a Short/Reel, private,
  description links work).

## 7. Run it end to end, by hand

- Press the button for one full video, watch the result, publish it yourself.
- Only after several clean runs consider a schedule.

## 8. Operations

- Error reporting, backups, moving to another computer: see [04-operations.md](04-operations.md).

## How to build each piece

- **Logic you write** (validators, title builders, image matching, caption timing): test-first. Write
  the test for the behaviour, watch it fail, then write the code. Pure functions are easy to test
  without any service running.
- **Integrations** (calling TTS, render, upload): test against the real service with real data, one
  stage at a time, and keep the test commands so you can repeat them.
- **Before saying something works**, run it and look at the output. "It should work" isn't evidence.
