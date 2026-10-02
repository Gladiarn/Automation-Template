# YouTube Shorts

Checked October 2026. Official docs: [YouTube Data API](https://developers.google.com/youtube/v3),
[videos.insert](https://developers.google.com/youtube/v3/docs/videos/insert),
[API Services Terms](https://developers.google.com/youtube/terms/api-services-terms-of-service).

A video is treated as a Short when it's vertical (or square) and within the Shorts length limit. There's
no separate Shorts upload API: you upload a normal video with `videos.insert`.

## Accounts

1. **A dedicated Google account** for the channel (not your personal one). Create the YouTube channel on it.
2. **A Google Cloud project** under that same account: [console.cloud.google.com](https://console.cloud.google.com).
3. Enable **YouTube Data API v3** (APIs & Services → Library).

## OAuth: letting your automation upload

1. **Google Auth Platform → Branding**: app name, support email. **Don't upload a logo**: a logo makes
   Google require a full verification review.
2. **Audience**: user type **External**. While the app is in **Testing**, add your channel account as a
   test user.
3. **Clients → Create client → Web application**. Add your orchestrator's OAuth redirect URI (n8n shows
   it in the credential form, for example `http://localhost:5678/rest/oauth2-credential/callback`).
4. Put the client ID and secret into your orchestrator's YouTube credential and sign in with the channel
   account. Google shows "Google hasn't verified this app": that's expected for your own app; choose
   **Advanced → Go to (app name)**.

### Testing vs In production (important)

- In **Testing**, the sign-in token **expires after 7 days**. Uploads stop until you sign in again.
- To stop that, publish the app (**Audience → Publish app**). For that, Google wants:
  - a **home page** and a **privacy policy** URL on a domain you own, added on the Branding page,
  - that domain as an **Authorized domain**, verified in [Google Search Console](https://search.google.com/search-console).
- Free way: a GitHub Pages site. A free GitHub **organization** named after your channel gives you
  `https://<channel>.github.io`. Add a **URL prefix** property in Search Console (the "Domain" type needs
  DNS access you don't have on github.io) and verify it with the **HTML tag** method.
- The privacy policy must say what the app accesses, that data isn't sold or shared, that use of Google
  data follows the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy)
  including the Limited Use requirements, link the YouTube Terms of Service and Google Privacy Policy,
  explain how to revoke access, and give a contact email.
- After publishing, the app is "In production" but **unverified**. For an app only you use (under 100
  users), you don't need to submit it for verification; ignore the banner. **Sign in again once** in
  your orchestrator so the new long-lasting token replaces the 7-day one.

## Rules that shape your automation

- **Unaudited API projects can only upload private videos.** Uploads from a project that hasn't passed
  the [API compliance audit](https://support.google.com/youtube/contact/yt_api_form) are locked private.
  You make each one public yourself in YouTube Studio, which doubles as a review step. Auto-publishing
  public needs the audit.
- **Quota**: projects get a daily quota (10,000 units by default). Uploads are expensive compared with
  other calls. The cost per upload and whether uploads have their own allowance have changed over time:
  check **APIs & Services → YouTube Data API v3 → Quotas** in your project for current numbers.
- **Never retry an upload automatically.** A timeout doesn't mean it failed; a retry can post a duplicate.
- **Updating a video replaces whole sections.** `videos.update` with `part=snippet` replaces title,
  description, tags and category together: send all of them, or they're cleared. Sending `part=status`
  without values resets privacy settings. Some workflow tools' "update video" actions send an empty
  status part; call the API directly with `part=snippet` when you only change text.
- **Made for kids**: set `selfDeclaredMadeForKids` honestly; it changes comments and ads.
- **Altered or synthetic content**: YouTube asks creators to disclose realistic AI-generated content.
  Check the current rule for your format.

## Useful extras

- Create a **playlist per series** and add each part; link previous and next parts in descriptions.
- Put sources and image credits in the description.
- Default language and category on upload help YouTube place the video.
