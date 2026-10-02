# Scripts

**What it is:** the words that get spoken and shown. The script is where quality is won or lost:
everything after it only presents it.

## Options

| Source | Cost | Quality control | Notes |
|---|---|---|---|
| You write them | Free | Full | Slowest; best for expert niches |
| An AI chat (Claude, ChatGPT, Gemini) by hand: paste a prompt, copy the result | Free tiers exist | You read each one | Good balance. Keep the prompt in your repo so every script follows the same rules |
| An AI model's API, called by the automation | Pay per use (usually cents per script) | Only if you add a review step | Fully automatic; mistakes reach viewers unless you review |
| Public-domain texts (myths, fables, old books) retold | Free | You check the retelling | Retell in your own words; modern translations are copyrighted |
| Your own data (sports results, prices, events) | Free–paid | Automatic checks possible | Script is filled from a template |
| Reddit posts, other people's stories | Free | — | Copyright belongs to the authors; platforms treat it as reused content. Not recommended |

## Make the script structured

Ask for (or write) scripts in a fixed structure, for example JSON with a hook, a body split into scenes,
an ending, a title and a source. Structure lets the automation:

- time each image to the sentence it belongs to,
- validate length (word count ≈ seconds: about 2.3–2.6 spoken words per second),
- reject broken scripts with a clear message instead of a broken video.

Keep the prompt in the repo (for example in `flow.md`), with your rules: length, tone, accuracy,
no quoting copyrighted text, what the hook must do.

## What makes Shorts scripts work

The bundled `viral-youtube-shorts` skill covers this in depth: a hook in the first seconds, no slow
introductions, an ending that makes a replay feel natural, and calls to action that name the next
video rather than asking for a subscribe.

## Ask yourself

1. Who reads every script before it becomes a video, and how long does that take per script?
2. What are my non-negotiable rules (accuracy, sources, tone, words to avoid)? Are they written down?
3. What happens when a script is bad: does the automation stop with a clear error?
