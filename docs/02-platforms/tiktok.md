# TikTok

Checked October 2026. Official docs: [Content Posting API: get started](https://developers.tiktok.com/doc/content-posting-api-get-started),
[Direct Post reference](https://developers.tiktok.com/doc/content-posting-api-reference-direct-post).

## Setup

1. A TikTok account for the channel.
2. A developer account at [developers.tiktok.com](https://developers.tiktok.com), then an **app** with the
   **Content Posting API** product and the `video.publish` (Direct Post) and/or `video.upload` scopes.
3. Your automation signs in with OAuth (Login Kit) and gets a token for the channel account.

## Two ways to post

- **Upload (to inbox)**: the video lands in the TikTok app as a draft notification; you finish and post
  it by hand. Good as a review step.
- **Direct Post**: the API publishes the video with the caption and settings you send.

## The audit (important)

Until your app passes TikTok's **audit**:

- Direct Post is limited to a few users per day, and **every post is forced to private (`SELF_ONLY`)**,
  whatever privacy you request. The account may also need to be private when posting.
- After passing the audit, posts can be public.

So for a start: use the inbox upload and post by hand, or post privately and change visibility in the app.
Apply for the audit once your integration works and follows TikTok's terms; the audit reviews how your app
presents posting settings to the user.

## Rules that shape your automation

- Your app must let the poster pick privacy and interaction settings and must show the creator's
  information before posting; TikTok's guidelines describe the required UX.
- Check TikTok's rules on AI-generated content labels and on unoriginal or reposted content.
- Rate limits apply per user; check the current numbers in the docs.
