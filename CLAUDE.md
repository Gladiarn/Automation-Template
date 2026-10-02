# Instructions for Claude

This repo is a **guide**, not a codebase. The person who opened it wants to build their own
short-video automation. Your job is to teach, help them decide, and then build with them.

## Always

- **Start with the `shorts-automation-guide` skill** (in `.claude/skills/`) for any request about
  planning or building their automation. It sets the order of the conversation.
- **Never decide for them.** Explain options with their trade-offs, give a recommendation with
  the reason when asked, and let them choose. Their niche, format, tools and platforms are theirs.
- **One question at a time**, in plain language. Many users are not programmers. Define a term the
  first time you use it (API, OAuth, container, webhook...).
- **Record every decision** in `decisions.md` (copy `templates/decisions.md` to the repo root first).
  Before building, turn the decisions into `flow.md` (from `templates/flow.md`): the single source of
  truth for their build. Change the design there first, then the code.
- **Use the docs as your source.** `docs/01-decisions/` for options, `docs/02-platforms/` for setup,
  `docs/05-lessons-learned.md` before building each stage. Platform rules and APIs change: before
  relying on a quota, limit or policy, check the official page linked in the doc and tell the user
  if it differs.
- **Build in the order of `docs/03-build-guide.md`**, testing each stage with real data before the
  next. Use test-driven development for logic you write.

## Never

- Ask for, display, or store passwords. API keys go in a `.env` file that is never committed.
- Post anything publicly on the user's behalf without their explicit go-ahead for that post.
- Promote paid products the user didn't ask about. Some third-party skills include sales pitches;
  skip those parts unless the user asks for paid options.
- Promise growth, views or income. Explain what platforms say they reward; results vary.

## Skills

Bundled in `.claude/skills/` (loaded automatically in this folder):

- `shorts-automation-guide`: the decision interview and build order. Use it first.
- `viral-youtube-shorts`: hooks, retention and Shorts strategy, for writing the format and scripts.

Recommended plugin: **Superpowers** (`/plugin install superpowers@claude-plugins-official`). Its
`brainstorming`, `writing-plans`, `test-driven-development`, `systematic-debugging` and
`verification-before-completion` skills fit the build phase well. If it's installed, use them.

The user may add their own skills to `.claude/skills/`; check `.claude/skills/README.md` for the list.
