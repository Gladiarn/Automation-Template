# Hosting

**What it is:** the computer that runs the tools.

## Options

| Option | Cost | Notes |
|---|---|---|
| Your own computer | Free | Only works while it's on. Fine for button-triggered runs |
| Windows with WSL2 (Ubuntu) | Free | Install **Docker Engine inside WSL**, or Docker Desktop. Both work; Engine-in-WSL avoids Desktop's licence and overhead |
| A spare PC / mini PC at home | One-time | Always on; low power |
| A VPS (Hetzner, DigitalOcean, etc.) | About $5–20/month | Always on, reachable from anywhere; rendering needs 2+ CPU cores and 4+ GB RAM |
| Cloud functions / serverless | Varies | Awkward for long FFmpeg renders; better for small steps |
| **GitHub Actions scheduled job** | Free (private repo: 2,000 min/month) | Your PC can be off. A fresh machine runs your script once a day, then disappears. No n8n/Docker needed. See below |

## Free and fully automatic: a daily GitHub Actions job

For "post one video a day with nobody involved", a scheduled GitHub Actions workflow works well and costs nothing:

- **How:** a workflow with `on: schedule` cron lines runs one script (write → voice → visuals → render → upload).
  A 10–15 minute run every day uses about 450 of the 2,000 free minutes a private repo gets each month.
- **Retries without double posts:** schedule 3–4 tries per evening; each run first checks "already posted today?"
  and exits in seconds if so. Record the upload in the repo **right after** uploading (the workflow commits it).
- **Pick cron times carefully:** cron is UTC only. Make sure every try falls on the same local calendar day in
  both summer and winter time, or one "evening" try can land on tomorrow's date.
- **State lives in the repo:** posted list, story records, music and fallback images. The daily commit also keeps
  GitHub from switching the schedule off after 60 days without activity.
- **Secrets** (API keys, the YouTube refresh token) go in the repo's Actions secrets, never in the code.
- **Pin a current Node version** (22+) on the runner, and test the same versions locally (a container with the
  same tools catches missing packages before the first scheduled run does).
- **Failures email you** automatically; a failed run must never post a half-finished video.
- Limits: runs can start some minutes late at busy times, the job has a time limit you set, and free-tier AI
  services can be busy or change their limits.

## Running the stack

Put every tool in one `compose.yaml` (Docker Compose): one command starts everything, the same way on any
machine. Good habits:

- Pin image versions (not `latest`) for tools whose API you depend on, and upgrade on purpose.
- `restart: unless-stopped` so services come back after a reboot.
- Keep data in folders next to the compose file (bind mounts), so backups are just folders.
- Pin the compose project name (`name:` at the top) so renaming the folder doesn't create a second stack.
- On Linux and WSL, `host.docker.internal` needs `extra_hosts: ["host.docker.internal:host-gateway"]`.

## Reaching it from outside

Not needed for button-triggered runs on your own machine. If you need webhooks from the internet or want
to use the forms from your phone, use a tunnel (for example Cloudflare Tunnel) rather than opening ports.

## Ask yourself

1. Does it need to run when my computer is off?
2. Is my machine strong enough to render (CPU, RAM, disk)?
3. If this machine died today, how would I rebuild? (See [04-operations.md](../04-operations.md).)
