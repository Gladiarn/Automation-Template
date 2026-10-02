# Facebook Reels and Instagram Reels

Checked October 2026. Meta changes these requirements often; treat this page as a map and confirm
details in the official docs:
[Instagram content publishing](https://developers.facebook.com/docs/instagram-platform/content-publishing),
[Facebook Reels publishing](https://developers.facebook.com/docs/video-api/guides/reels-publishing).

## Shared setup

1. A **Meta developer account** at [developers.facebook.com](https://developers.facebook.com) and an **app**.
2. Your own accounts can use the app while it's in development mode if they have a role on the app
   (admin, developer or tester). **App review** is needed before other people's accounts can use it.
3. Your automation signs in with OAuth and gets an access token. Tokens expire; plan how you refresh them
   (long-lived tokens, and a reminder before they run out).

## Instagram Reels

- Needs an Instagram **professional account**. Sources disagree on whether Creator accounts work and
  whether a linked Facebook Page is required; it depends on which login flow you use (Instagram Login
  vs Facebook Login). Check the current content-publishing page before you set up the account.
- Permissions: the `instagram_business_content_publish` family (older `instagram_content_publish` names
  were replaced in 2025).
- Publishing is three steps: create a media container with `media_type=REELS` and a **public video URL**,
  wait until its status is `FINISHED`, then publish it.
- The video must be reachable at a public URL while Instagram fetches it: plan your storage for that.
- Limit: a fixed number of API-published posts per account per 24 hours (50 when checked).

## Facebook Page Reels

- Posting goes to a **Facebook Page** (not a personal profile), with a Page access token from a user who
  can create content on that Page.
- Permissions: `pages_show_list`, `pages_read_engagement`, `pages_manage_posts`.
- Endpoint: `POST /{page_id}/video_reels` (start upload, upload, finish/publish).
- Video: MP4, 9:16, 1080×1920 recommended, 3–90 seconds; limit of 30 API-published reels per Page
  per 24 hours when checked.

## Rules that shape your automation

- Meta labels some AI-generated content and has rules on unoriginal content; check both.
- Reels longer than the platform's Reels limit may be posted as regular videos instead.
