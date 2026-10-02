# Voice

**What it is:** turning the script into speech. Most faceless channels use text-to-speech (TTS).

## Options

| Tool | Cost | Runs | Quality | Notes |
|---|---|---|---|---|
| [Kokoro](https://github.com/remsky/Kokoro-FastAPI) (Kokoro-FastAPI) | Free, open source | Your computer (CPU is fine; GPU faster) | Very good for its size | Several English voices; returns **word timestamps**, which makes exact captions easy |
| [Piper](https://github.com/rhasspy/piper) | Free, open source | Your computer, very light | Good | Many languages; runs on a Raspberry Pi |
| Coqui XTTS | Free to run | Your computer, needs a good GPU | Very good, voice cloning | Check the model licence before commercial use |
| ElevenLabs | Paid (free tier is small) | Cloud API | Excellent | Most natural; costs grow with volume |
| OpenAI / Google / Azure TTS | Pay per character | Cloud API | Very good | Reliable; small cost per video |
| Your own recording | Free | — | Yours | Most original; can't be fully automated |

## How to choose

- **Budget zero and decent hardware** → a local open-source engine.
- **Voice is the brand** (storytelling, ASMR-like niches) → test the paid voices; listen to a full
  60-second script, not one sentence.
- **Captions need exact timing** → prefer an engine that returns word timestamps, or plan a separate
  transcription step (see [captions.md](captions.md)).

## Gotchas

- Generate speech **per sentence or per scene**, not the whole script at once. Then you know exactly
  how long each part lasts, and images switch on the right sentence.
- Quotation marks and unusual punctuation can be read oddly or leak into captions. Clean text before TTS.
- Names and foreign words get mispronounced. Keep a small replacement list (spelling the TTS reads
  correctly) and apply it only to the speech, not to the captions.
- AI voices may need a disclosure label on some platforms when the content is realistic. Check each
  platform's current AI-content rules.

## Ask yourself

1. Have I listened to a full video's worth of this voice and still liked it?
2. Can it say the names and words my niche uses?
3. What does it cost at 1 video a day for a year?
