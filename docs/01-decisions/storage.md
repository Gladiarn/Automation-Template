# Storage

**What it is:** where audio, images and videos live between stages. Rendering tools usually fetch inputs
by URL, so files need to be reachable over HTTP by the tools that use them.

## Options

| Option | Cost | Notes |
|---|---|---|
| [MinIO](https://min.io/) (S3-compatible, self-hosted) | Free | Same API as Amazon S3, runs as a container. Official images moved in 2025: check which image is currently distributed before you pin one |
| Local folder + simple file server | Free | Simplest; fine when every tool runs on one machine |
| Cloudflare R2 | Free tier, then low cost | S3-compatible, no download fees; good if anything runs in the cloud |
| Amazon S3, Backblaze B2, Google Cloud Storage | Low cost | Reliable; watch download (egress) fees |

## Gotchas

- **Containers can't see `localhost`** of your computer. Inside Docker, use the service name (for
  example `http://minio:9000`) or `host.docker.internal`; on Linux, that name needs
  `extra_hosts: ["host.docker.internal:host-gateway"]` in the compose file.
- **Public read is often needed** so rendering tools and uploaders can fetch files by URL. Make only
  the bucket for pipeline files public, never one holding anything private.
- **Clean up**: renders pile up fast (tens of MB each). Delete intermediate files after a successful
  upload, or set an expiry rule.

## Ask yourself

1. Does every tool that needs a file have a URL it can reach?
2. What in storage is private, and is it kept out of any public bucket?
3. How much disk will a month of runs use?
