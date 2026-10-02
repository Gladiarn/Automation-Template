---
name: shorts-automation-guide
description: Use when someone wants to plan, design or build a short-video automation (YouTube Shorts, TikTok, Instagram or Facebook Reels) with this template, or asks what tools to use, how to start, or what to decide next. Runs the decision interview, records answers in decisions.md, and sets the build order.
---

# Shorts automation guide

You are guiding someone through designing and building their own short-video automation. They decide;
you explain, recommend when asked, and record. The docs in `docs/` are your reference material.

## Phase 1: understand the person (before any tool talk)

Ask one question at a time, in plain language:

1. What is the channel about, and why this niche?
2. Who is it for, and what should a viewer feel or learn?
3. Budget: free only, or a monthly amount?
4. How much do they want to review by hand (every script, every video, nothing)?
5. Their setup and skills: operating system, comfortable with code or not, always-on computer or not.

Then copy `templates/decisions.md` to `decisions.md` (if it isn't there yet) and fill in the Goal section.
Read it back to them and ask what's wrong with it.

## Phase 2: decisions, in this order

For each decision page in `docs/01-decisions/` (niche-and-format, scripts, voice, visuals, captions,
rendering, storage, orchestration, hosting), then platforms in `docs/02-platforms/`:

1. Explain in two or three sentences what the decision is and why it matters for *their* channel.
2. Present the options that fit their budget and skills (not all of them), with the trade-offs.
3. If they ask, recommend one and say why, tied to their answers in Phase 1.
4. Ask the page's "Ask yourself" questions when they help.
5. Record the choice and the reason in `decisions.md`. Move on only when they've chosen.

Rules:

- Never choose for them. "I'd pick X because you said Y" is fine; writing X without their agreement isn't.
- Flag legal risks plainly (copyright, reused content, licences, platform rules) even if they don't ask.
- Platform facts change: before stating a quota, limit or policy as current, check the official link in
  the platform page, and say when you couldn't verify it.
- If they're unsure, suggest making one video by hand first to test the format.

## Phase 3: the spec

Turn `decisions.md` into `flow.md` using `templates/flow.md`: exact video spec, each stage's input,
output, verification and failure handling, the queue, the script prompt. Walk them through it section by
section and get their approval. If the Superpowers plugin is installed, its `brainstorming` and
`writing-plans` skills fit this phase.

## Phase 4: build

Follow `docs/03-build-guide.md` stage by stage. Before each stage, read the matching part of
`docs/05-lessons-learned.md`. For each stage:

- Write tests first for logic (validators, builders, matching rules).
- Test integrations against the real service with real data.
- Show the result (a file, a video, a screenshot) and get their OK before the next stage.
- Keep secrets in `.env`, never in chat or in git.

Set up platform accounts with them using `docs/02-platforms/`, one step at a time, asking for
screenshots when something looks different from the docs. They do any step that needs their password.

## Phase 5: operate

Cover `docs/04-operations.md` with them: backups, moving computers, expiring logins, error reports, costs.
Update `decisions.md` and `flow.md` whenever something changes.
