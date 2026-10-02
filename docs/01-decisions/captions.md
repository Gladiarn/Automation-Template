# Captions

**What it is:** the words on screen. Most Shorts are watched without sound at first, so captions carry
the video for many viewers.

## Getting word timings

| Method | Accuracy | Notes |
|---|---|---|
| Word timestamps from the TTS engine (for example Kokoro-FastAPI) | Exact | Easiest when available: you know which word is said when |
| Transcribe the audio with Whisper (or whisper.cpp, faster-whisper) | Very good | Works with any voice, including your own; spelling may differ from your script |
| Estimate from text length | Rough | Fine for whole-sentence captions, poor for word-by-word |

Use **your script's spelling** for the displayed words, and the timestamps only for timing. Transcription
can misspell names.

## Styles

- **Word-by-word highlight** (the current word in a different colour): the most common Shorts style.
- **Short phrases** (2–4 words at a time): easier to read, calmer.
- **Full sentences**: for slower, reflective content.

Captions are usually rendered as an ASS subtitle file (supports colours, outlines, per-word timing) and
burned into the video with FFmpeg.

## Placement

Platform buttons and text cover parts of the screen. Keep captions and logos in the middle area:
roughly avoid the **top 15–20%** and the **bottom 20–25%** of a vertical video, and the right edge where
like/comment buttons sit. Check a finished video on a phone in each app.

## Ask yourself

1. Can someone follow the whole video with the sound off?
2. Are the captions readable on a small phone, over both bright and dark images?
3. Do names appear spelled correctly?
