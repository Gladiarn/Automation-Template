# Operations

## Secrets

- All keys and passwords in **`.env`**, listed in `.gitignore` before your first commit. Commit a
  `.env.example` with the names only.
- Generate random values for anything you invent (storage passwords, API keys between your own services).
- **Watch your logs and terminals**: some tools print secrets when they create them (for example a
  storage tool printing a new secret key). Silence that output in scripts.
- Never put a real password in a chat with an AI assistant. If a key leaks, replace it.

## Backups and moving to a new computer

What can't be recreated from your repo:

- `.env` (secrets),
- your orchestrator's database (workflows, the queue, platform logins, and the key that encrypts them),
- anything you made by hand in a tool's UI.

A good pattern: an **encrypted snapshot file committed to the repo**. One command packs `.env` and the
orchestrator's database, encrypts it with a passphrase (for example AES-256-GCM with a key derived by
scrypt), and writes one file you commit. On the new computer: clone, run the matching load command,
enter the passphrase. Keep the passphrase in a password manager, never the same as an account password.

- Stop the orchestrator for a few seconds while copying its database, so the copy is consistent.
- Don't snapshot while a finished video is waiting to upload if that video lives in storage that the
  snapshot doesn't include.
- Script any one-time setup (storage buckets, keys, public-read rules) so a new computer is one command
  away, not a page of notes.
- Run the system on **one computer at a time**: two copies would both work the same queue.

## Logins that expire

| Platform | What expires | What to do |
|---|---|---|
| YouTube, app in Testing | Token after 7 days | Publish the app (see youtube.md), then sign in once more |
| YouTube, app in production | After ~6 months unused, or if you revoke access | Sign in again |
| Meta (Facebook/Instagram) | Access tokens expire | Use long-lived tokens; set a reminder |
| TikTok | Access and refresh tokens expire | Your orchestrator refreshes; re-authorize if refresh fails |

## Monitoring

- Every failure marks the video `failed` with the step and message.
- An error workflow or script that notifies you (email, chat message) when a run fails.
- Check disk usage monthly; delete old renders.

## Costs

Write your monthly cost down in `decisions.md`: hosting, paid APIs per video × videos per month, domain
if any. Free tiers change: re-check them when a platform emails you about pricing.
