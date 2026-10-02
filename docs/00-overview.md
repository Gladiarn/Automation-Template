# Overview: what a Shorts automation is made of

Every automated short-video channel, whatever the niche, runs the same chain of stages. You choose
how each stage is done; some stages you may skip or do by hand.

```
 idea ──► script ──► voice ──► visuals ──► captions ──► render ──► storage ──► upload
  │         │          │          │            │           │          │          │
 you or   you, an    text-to-   images,     word-by-    combine    hold the   post to
 a list   AI model,  speech or  clips,      word text   it all     files      YouTube,
          or a       your own   text cards  timed to    into one   between    TikTok,
          source     recording  or gameplay the voice   vertical   stages     Instagram,
                                                        video                 Facebook
                     └───────────── orchestrator: runs the stages, keeps the queue ─────────┘
```

| Stage | Question it answers | Decision page |
|---|---|---|
| Niche and format | What are the videos about, and what do they look like? | [niche-and-format.md](01-decisions/niche-and-format.md) |
| Script | Where does the text come from, and who checks it? | [scripts.md](01-decisions/scripts.md) |
| Voice | Who or what speaks it? | [voice.md](01-decisions/voice.md) |
| Visuals | What is on screen? | [visuals.md](01-decisions/visuals.md) |
| Captions | How do the words appear on screen? | [captions.md](01-decisions/captions.md) |
| Render | What tool assembles the final video? | [rendering.md](01-decisions/rendering.md) |
| Storage | Where do files live between stages? | [storage.md](01-decisions/storage.md) |
| Orchestration | What runs the stages, in what order, and what happens on failure? | [orchestration.md](01-decisions/orchestration.md) |
| Hosting | Which computer runs it all? | [hosting.md](01-decisions/hosting.md) |
| Platforms | Where it's posted, and how the accounts and APIs are set up | [02-platforms/](02-platforms/) |

## Words used in this guide

- **API**: a way for programs to talk to a service, for example "upload this video to YouTube".
- **Self-hosted**: running a tool on your own computer or server instead of paying a service.
- **Container (Docker)**: a packaged tool that runs the same way on any computer. Most tools here run
  as containers, started together from one file (`compose.yaml`).
- **OAuth**: how a platform lets your automation act on your account without your password. You sign
  in once; the platform gives the automation a token.
- **Queue**: the list of videos to make, each with a status (to make, made, uploaded, failed).
- **Orchestrator**: the tool that runs the stages in order, keeps the queue and reports failures.

## How much is automated is your choice

Fully automatic (a schedule makes and posts videos without you) is possible but risky: a bad script,
a wrong image, or a broken caption goes out before anyone sees it. Many channels keep a human step:

- **Human writes or approves the script**, the machine does the rest.
- **Machine makes the video, human watches it** and then presses "upload" or "publish".
- **Uploads go out private or as drafts**, a human makes them public.

On YouTube, an API project that hasn't passed Google's audit can only upload **private** videos anyway,
so a "review then publish" step comes for free. See [02-platforms/youtube.md](02-platforms/youtube.md).

## Next

Copy [templates/decisions.md](../templates/decisions.md) to the repo root as `decisions.md`, then
work through [01-decisions/](01-decisions/) starting with niche and format.
