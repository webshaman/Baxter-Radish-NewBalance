# Plan 002 — Move deck videos to Cloudflare Stream

**Scope:** All decks in this repo, starting with `/volume/`, then `/mbm/`.
**Destination:** `./plans/plan-002-cloudflare-stream-video-hosting.md`
**Date:** 2026-10-05

## Problem
The `/mbm/` placement videos are plain MP4s committed to git (`mbm/assets/placements/`,
~75 MB across 11 files) and served as static files by Vercel into a native `<video>` tag.
- Every play is Vercel bandwidth, so it adds to Vercel costs.
- No adaptive bitrate: slow connections download the full-quality file.
- Each new deck with its own videos permanently grows the git history (no LFS).

We regularly receive loose video files (Dropbox folders and similar) that aren't on YouTube,
so this needs to be a repeatable upload step, not a one-off.

## Decision
Host deck videos on **Cloudflare Stream**.

YouTube was considered and rejected:
- API uploads from an unaudited Google Cloud project are forced to private, so "unlisted"
  needs a compliance audit first (weeks).
- videos.insert quota allows only a handful of uploads per day.
- These are third-party ads with major-label music, so Content ID claims or copyright strikes
  could land on the Baxter House channel.
- YouTube player chrome and end-screen suggestions inside the deck modal.

Cloudflare Stream gives adaptive HLS/DASH playback, a clean embeddable player, no content
matching, and usage-based pricing on the order of a few dollars a month at our volume.

## Credentials
Amit is adding the Cloudflare credentials to **Doppler**. Claude reads them from there (or
from environment secrets in claude.ai cloud sessions); nothing is committed to the repo.
- `CLOUDFLARE_ACCOUNT_ID`
- `CLOUDFLARE_STREAM_API_TOKEN` — API token scoped to *Stream: Edit*
- Locally: `doppler run -- <command>`.
- Cloud sessions: the same values as environment secrets, and the environment's network
  access must allow `api.cloudflare.com`, `*.cloudflarestream.com` and
  `upload.videodelivery.net`.

## Workflow (each time new videos arrive)
1. Videos land in a local folder (Amit downloads them, or Claude fetches them when the source
   host is reachable).
2. A repo script (planned: `scripts/stream-upload`) for each file:
   - uploads to Stream (tus resumable upload for large files, or "upload from URL"),
   - tags it with deck name and title metadata,
   - waits until it is ready to stream,
   - prints the video UID, thumbnail URL and iframe embed URL.
3. The deck's placement cards and modal `ITEMS` entries point at the Stream iframe
   (`https://customer-<code>.cloudflarestream.com/<uid>/iframe?autoplay=true`) and the
   Stream thumbnail, so no MP4s or thumbnails are committed.
4. Card titles come from the file names or a small manifest (brand, spot title, artist).

## Rollout
1. **Volume** (`/volume/`): upload the work from Amit's Dropbox link and fill the empty
   Music Supervision Placements slide. Blocked until the credentials are in Doppler and the
   files are available.
2. **MBM** (`/mbm/`): upload the 11 existing placement videos, switch the cards and modal
   entries to Stream embeds, delete `mbm/assets/placements/*.mp4` from the tree.
3. Use the same script for every future deck; never commit video files again.

## Open questions
- The Stream customer subdomain (`customer-<code>`) comes from the Cloudflare dashboard;
  confirm it once the account is set up.
- Whether to purge existing MP4s from git history (rewrite) or just stop adding new ones.
  Default: just stop adding; a history rewrite isn't worth the disruption.
