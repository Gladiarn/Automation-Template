# Visuals

**What it is:** what's on screen while the voice speaks. The legal side matters most here: you need the
right to use every image and clip.

## Options

| Source | Cost | Licence | Notes |
|---|---|---|---|
| Public-domain art: [Wikimedia Commons API](https://commons.wikimedia.org/w/api.php), [The Met Open Access](https://metmuseum.github.io/), [Art Institute of Chicago API](https://api.artic.edu/docs/), Rijksmuseum | Free | Public domain or CC0 (check per file) | Great for history, myths, religion, art. Matching an image to a specific scene is the hard part |
| Stock: [Pexels](https://www.pexels.com/api/), [Pixabay](https://pixabay.com/api/docs/) | Free with API key | Their own free licences | Good for generic scenes; read their terms on attribution and use in videos |
| AI-generated images or video | Paid per image, or free-tier quotas | Depends on the service's terms | Exactly matches the script; quality and style vary; free quotas run out fast; may need AI labels |
| Background footage (gameplay, satisfying clips) | Free–paid | Only footage you're licensed to use | Low effort; check the licence of every clip and the platform's reused-content rules |
| Text cards, shapes, charts | Free | Yours | Rendered by your own templates |
| Your own photos and footage | Free | Yours | Most original |

## Rules that save you trouble

- **Check the licence through the API**, per file, and store the credit (title, author, source).
  Put credits in the video description. Reject anything without a clear licence.
- **Verify every download**: compare the size with the server's `Content-Length` and make sure the
  image decodes. A half-downloaded image can render as a solid block of colour.
- **Filter for your audience**: classical art includes nudity; stock and AI images can include text,
  logos or watermarks. Filter by title or tags, and review videos before they go public.
- **Make scenes match**: search with specific phrases per scene (who, what moment), and require the
  result's title or tags to contain the key subject words, not just any word from the search.
- **Keep a reviewed fallback pool**: a handful of safe, on-theme images to use when nothing matches.
- **Minimum resolution**: vertical 1080×1920 needs reasonably large sources (about 1000 px on the short
  side as a floor); small images look blurry once panned or zoomed.

## Ask yourself

1. For any image in my video, can I show where it came from and why I'm allowed to use it?
2. What happens when the search finds nothing, or the wrong thing?
3. Does the style stay consistent from video to video?
