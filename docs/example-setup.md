# Example setup

One real combination of choices, to show how the decisions fit together. **It's an example, not a
recommendation**: your niche and constraints will lead somewhere else.

| Decision | Choice | Why |
|---|---|---|
| Niche and format | Mythology retold as multi-part narrated stories over public-domain paintings | Endless public-domain material; accuracy checkable against ancient sources |
| Constraint | Free only: no paid APIs or subscriptions | Owner's rule |
| Scripts | Owner pastes a fixed prompt into a free AI chat; the reply is structured JSON with hook, scenes, ending, title, source | Owner reviews every story; structure lets the automation time scenes |
| Voice | Kokoro (self-hosted, CPU) | Free, good storyteller voice, word timestamps |
| Visuals | Public-domain paintings from Wikimedia Commons and a museum API, licence-checked; reviewed fallback pool | Free, legal, fits the subject |
| Captions | Word-by-word highlight, ASS file from TTS word timestamps, script spelling | Exact timing, correct names |
| Render | NCA Toolkit (FFmpeg behind an HTTP API) | Callable from a no-code orchestrator |
| Storage | MinIO (S3-compatible, self-hosted) | Render tool reads inputs by URL |
| Orchestration | n8n, workflows generated from code; three forms: add story, make next video, upload next video | Visual debugging, built-in queue table, YouTube node |
| Hosting | Owner's Windows PC, WSL2 Ubuntu with Docker Engine; started by hand | Free; button-triggered runs don't need an always-on server |
| Platform | YouTube Shorts, uploaded private; owner watches and publishes | Unaudited API uploads are private anyway; doubles as review |
| Operations | Encrypted snapshot in the repo for moving computers; GitHub Pages home + privacy policy to publish the Google app | No weekly re-login; rebuild from a clone |

What the owner does per video: press **Make**, watch the result, press **Upload**, then switch it to
public in YouTube Studio.
