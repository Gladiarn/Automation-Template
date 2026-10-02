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
