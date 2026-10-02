# Lessons learned

Gotchas from building a real narrated-Shorts automation (self-hosted n8n, Kokoro TTS, NCA Toolkit,
MinIO, YouTube). Each cost real time once. Most apply to any stack.

## Downloads and free APIs

- **Verify every download.** Slow servers (Wikimedia can drop to ~20 KB/s) cut files short; a truncated
  JPEG rendered as a solid green block. Compare bytes with `Content-Length`, check the image decodes,
  use generous timeouts, retry.
- **Free APIs sometimes reply empty or with HTTP 429** (too many requests). Retry with growing pauses,
  wait out 429s, pause between downloads, and send a descriptive `User-Agent` (Wikimedia asks for one).
- **APIs retire endpoints.** A museum API's search endpoint was retired mid-build; the replacement was a
  new version path. Keep endpoint URLs in one place and check release notes when something breaks.
- **"Too small" filters can reject most good results.** A 1500 px minimum rejected many real paintings;
  1000 px worked. Measure on real searches before fixing a threshold.

## Matching images to scenes

- Requiring one shared word between the search and the title let wrong images through (a painting of a
  different myth matched on one common word). Requiring **two subject words** (or all of them when
  there are fewer) fixed it. Artist names and generic words ("painting") don't count as subject words.
- Titles from Wikimedia carry junk: Wikidata markup (`label QS:...`), language prefixes ("German: ..."),
  sometimes two languages. Clean titles before using them in credits.
- Filter medals, coins, plaques, photos and sketches when you want paintings. Review the fallback pool
  by eye: a "safe" search still returned nudes, photos and the wrong country.

## Audio, captions, rendering

- Generate speech **per beat** (hook, each scene, ending) so images switch on the right sentence.
- Take caption **timing** from the TTS word timestamps but caption **text** from the script.
- Quotation marks in a spoken line came back as stray punctuation in captions. Strip them from lines
  the automation adds.
- A render API's "concatenate audio" endpoint only accepted MP3; joining WAVs with FFmpeg's concat
  filter inside the compose step worked instead.
- Keep logos and captions out of the top ~20% and bottom ~25% of the frame: platform UI covers them.

## n8n specifics

- Generate workflows from code and deploy through the API; never hand-edit deployed workflows.
- Webhooks register a moment **after** activation: the first call can 404. Poll until it answers.
- The Code node sandbox lacks some browser/Node globals (for example `URLSearchParams`). Build query
  strings by hand, and test library code in a sandbox that matches.
- Data Table inserts reject unknown columns; don't add helper fields to rows you insert.
- Node parameters change between versions (where a form's path goes, which completion node version,
  required `resource` fields). Check the node definitions of your installed version.

## YouTube

- The upload node returned the new video's ID as `uploadId`, not `id`: the next step (add to playlist)
  failed until that was fixed. Check real outputs, not assumptions.
- A workflow tool's "update video" action also sent an empty `status` part, which would reset privacy
  settings. Use a direct `part=snippet` update for text changes.
- Updates appear in API reads with a short delay; re-read before concluding an update failed.
- Never retry uploads automatically.
- OAuth in Testing expires weekly; publishing the app needs a home page and privacy policy (a free
  GitHub Pages site works).

## Infrastructure

- An official container image disappeared from public registries (MinIO, 2025). Keep a note of which
  image you use and why, and pin the version.
- On Linux/WSL, `host.docker.internal` needs `extra_hosts: host-gateway`.
- Files a container writes may belong to its internal user (for example uid 1001); fixing permissions
  needs `sudo`.
- Pin the compose project name so renaming the folder doesn't orphan containers.
- Command-safety hooks in AI coding tools can block harmless commands by keyword (a script called
  "restore" was mistaken for `git restore`). Name scripts to avoid destructive-sounding words.

## Process

- Manual buttons beat schedules at first: the owner pressed "make" and "upload", watched each video,
  then published it.
- Series parts must go out in order; a part's "next part" link can only be added after the next part
  is uploaded, so update the previous description at that moment.
- Write the design down first and change it there first; it kept a long build consistent across many
  sessions.
