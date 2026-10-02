# Rendering

**What it is:** assembling voice, visuals, captions and music into one vertical video file
(1080×1920, H.264 video, AAC audio, MP4).

## Options

| Tool | Cost | Skill needed | Notes |
|---|---|---|---|
| [FFmpeg](https://ffmpeg.org/) directly | Free | Medium–high (command-line filters) | Does everything; every other tool below uses it underneath |
| [No-Code Architects Toolkit](https://github.com/stephengpope/no-code-architects-toolkit) (NCA) | Free, self-hosted | Low–medium | FFmpeg behind a simple HTTP API (compose, caption, concatenate…). Fits no-code orchestrators like n8n |
| [Remotion](https://www.remotion.dev/) | Free for individuals and small companies; company licence above that | Medium (React) | Videos as code with real layouts and animation; check its licence for your size |
| MoviePy (Python) | Free | Medium | Simple scripted editing in Python |
| Cloud render APIs (Shotstack, Creatomate, JSON2Video) | Paid | Low | JSON templates, no server to run; costs per minute rendered |
| CapCut / editors by hand | Free–paid | Low | Not automatable; fine for testing a format manually first |

## Things every render step needs

- **Exact timing**: each image or clip lasts exactly as long as its narration. Measure audio durations
  (or use the TTS timestamps) rather than guessing.
- **Motion on still images**: a slow pan or zoom (Ken Burns effect) keeps stills from looking static.
- **Verification**: after rendering, check the file downloads completely and has the expected duration.
- **Know each tool's input limits**: for example, some concatenate endpoints only accept one audio format.
  Read the docs of the exact endpoint you call.

Rendering on a CPU takes a few minutes per minute of video. That's fine for a few videos a day.

## Ask yourself

1. Do I want a no-code tool (an API I call) or code I write?
2. Can I describe one finished video precisely: sizes, fonts, colours, timings, logo position?
3. How will I know a render is broken before it's uploaded?
