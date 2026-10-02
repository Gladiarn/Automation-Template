# Flow: <channel name>

Design spec for the automation. **Single source of truth**: change the design here first, then the code.
Status: draft | approved (date)

## Goal

What one press of the button produces, and what "working" means.

## Hard rules

- Budget:
- Accuracy / sources:
- Rights: every word, image, clip and sound is ours to use because…
- Uploads are: private / draft / public

## Script structure

| Beat | Length | Example |
|---|---|---|
| Hook | | |
| Body (scenes) | | |
| Ending | | |
| Call to action | | |

Script prompt (if an AI writes or drafts scripts):

```
<the exact prompt>
```

## Video spec

| Property | Value |
|---|---|
| Length | |
| Resolution | 1080×1920, mp4, H.264/AAC |
| Voice | engine, voice name, speed |
| Captions | style, colours, position, words per line |
| Visuals | source, motion, per-scene timing |
| Logo / branding | file, size, position (inside the safe zone) |

## Stages

For each stage: input, what happens, output, how it's verified, what happens on failure.

1. Intake:
2. Voice:
3. Visuals:
4. Render:
5. Captions:
6. Upload:

## Queue

| Column | Purpose |
|---|---|
| id / status | queued → rendering → rendered → uploading → uploaded, or failed |
| | |

## Errors and retries

- Which calls retry, how many times:
- Uploads: never retried automatically.
- How a failure is reported:

## Known limits

- Platform quotas:
- Login expiry:

## Testing

How each stage is tested, and the end-to-end check before going public.
