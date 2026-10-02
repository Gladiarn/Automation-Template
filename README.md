<h1 align="center">Shorts Automation Template</h1>

<p align="center">
  <b>Learn how to build your own automation for YouTube Shorts, TikTok and Reels,<br>
  for any niche, with the tools you choose.</b>
</p>

<p align="center">
  <a href="#quick-start">Quick start</a> ·
  <a href="docs/00-overview.md">Overview</a> ·
  <a href="docs/01-decisions/">Decisions</a> ·
  <a href="docs/02-platforms/">Platforms</a> ·
  <a href="docs/05-lessons-learned.md">Lessons learned</a>
</p>

---

This is a **guide, not a product**. There's no code to install and no format forced on you. It explains
what a short-video automation is made of, the tools you can use for each part, how to choose between them,
how to set up each platform, and the mistakes that cost real time when someone built one.

**You decide** what your videos are about and how they're made. The guide helps you decide well, and,
if you use Claude Code, Claude walks you through every decision and builds it with you.

## Quick start

**Option A: let Claude guide you (recommended)**

1. Install [Claude Code](https://claude.com/claude-code).
2. Get the template and open it:

   ```bash
   git clone https://github.com/Gladiarn/Automation-Template.git my-shorts-automation
   cd my-shorts-automation
   claude
   ```

3. Say: **"Help me build my Shorts automation."**

Claude reads [`CLAUDE.md`](CLAUDE.md) and the bundled [skills](.claude/skills/), asks about your niche,
budget and setup one question at a time, explains the options in plain language, records your choices
in `decisions.md`, and then builds the automation with you, stage by stage.

**Option B: read it yourself**

1. Read the [overview](docs/00-overview.md) (10 minutes).
2. Copy [`templates/decisions.md`](templates/decisions.md) to `decisions.md` and fill it in while you go
   through the [decision pages](docs/01-decisions/), in order.
3. Set up your [platforms](docs/02-platforms/).
4. Follow the [build guide](docs/03-build-guide.md).

## How a Shorts automation works

```
 idea ──► script ──► voice ──► visuals ──► captions ──► render ──► storage ──► upload
                      └──────────── an orchestrator runs it all and keeps the queue ────────────┘
```

Every stage has options, from free and self-hosted to paid services. For each one this guide gives you
the trade-offs, the costs, the gotchas, and three questions to ask yourself before you pick.

## What you'll decide

| Decision | Examples of what you can choose from |
|---|---|
| [Niche and format](docs/01-decisions/niche-and-format.md) | Narrated stories over images, background footage, text cards, facts, series |
| [Scripts](docs/01-decisions/scripts.md) | You, an AI chat you review, an AI API, public-domain texts, your own data |
| [Voice](docs/01-decisions/voice.md) | Kokoro, Piper, XTTS (free) · ElevenLabs, cloud TTS (paid) · your own voice |
| [Visuals](docs/01-decisions/visuals.md) | Public-domain art, stock (Pexels, Pixabay), AI images, licensed footage |
| [Captions](docs/01-decisions/captions.md) | Word-by-word highlight, phrases, sentences; timing from TTS or Whisper |
| [Rendering](docs/01-decisions/rendering.md) | FFmpeg, NCA Toolkit, Remotion, MoviePy, cloud render APIs |
| [Storage](docs/01-decisions/storage.md) | MinIO, a local folder, Cloudflare R2, S3 |
| [Orchestration](docs/01-decisions/orchestration.md) | n8n, Activepieces, Make/Zapier, your own scripts |
| [Hosting](docs/01-decisions/hosting.md) | Your PC (Windows/WSL, Mac, Linux), a mini PC, a VPS |

## Platforms covered

| Platform | Guide | Good to know |
|---|---|---|
| YouTube Shorts | [youtube.md](docs/02-platforms/youtube.md) | Unaudited API uploads are private; a free GitHub Pages site stops the weekly re-login |
| TikTok | [tiktok.md](docs/02-platforms/tiktok.md) | Posts are private until your app passes TikTok's audit |
| Instagram and Facebook Reels | [facebook-instagram.md](docs/02-platforms/facebook-instagram.md) | Needs a Meta app and a professional account or Page |

## What's inside

```
├── CLAUDE.md                 How Claude should guide you
├── docs/
│   ├── 00-overview.md        The pipeline and the words used
│   ├── 01-decisions/         One page per decision
│   ├── 02-platforms/         YouTube, TikTok, Facebook/Instagram setup
│   ├── 03-build-guide.md     The order to build in, and how to test each stage
│   ├── 04-operations.md      Secrets, backups, moving computers, expiring logins, costs
│   ├── 05-lessons-learned.md Gotchas from a real build
│   └── example-setup.md      One real combination of choices
├── templates/
│   ├── decisions.md          Your choices and why
│   └── flow.md               Your build's design spec
└── .claude/skills/           Skills Claude loads automatically (add your own)
```

## What you'll need

- A computer that runs Docker (Windows with WSL2, macOS or Linux), or a small server.
- An account on each platform you'll post to, ideally one made just for the channel.
- A few focused days for a first working version, mostly platform setup and testing.

## Before you post

Every platform has rules about automated posting, reused content, AI labels and copyright, and they
change. An automation can break a rule many times before anyone notices, so read them first: each
platform page links to the official ones. Facts in this guide were checked in October 2026.

## Credits and license

MIT, see [LICENSE](LICENSE). Bundled skill `viral-youtube-shorts` © [Vyral](https://github.com/vyralcontent/content-skills), MIT.
Recommended plugin: [Superpowers](https://github.com/obra/superpowers) by Jesse Vincent, MIT.
Written from the experience of building the [Minutes Myth](https://github.com/minutes-myth) channel.
