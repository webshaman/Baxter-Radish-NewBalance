# Activity 002 — Plan 002: Volume and MBM videos on Cloudflare Stream

**Date:** 2026-10-06

## Completed
- Added `scripts/stream-upload`: uploads a folder of videos to Stream, tags each with deck, title and source file, skips files already uploaded for that deck, waits until ready, and writes `stream-manifest.json` with UID, iframe and thumbnail URLs.
- Downloaded the 22 Volume videos from Volume's Dropbox folder and uploaded them to Stream (deck `volume`).
- Uploaded the 11 existing MBM placement videos to Stream (deck `mbm`).
- `/volume/`: filled the Music Supervision Placements slide with 22 cards (Stream thumbnail at 25% of each video) and matching modal entries using the Stream player.
- `/mbm/`: switched the 11 cards and modal entries from local MP4s to the Stream player; kept the existing curated poster JPGs; removed `mbm/assets/placements/*.mp4` (75 MB) from the tree.
- Title cleanup from file names: "Discovery Channel - Shark Week" (typo in source), "PowerBar - Ryan's Redo", dropped doubled extensions.

## Notes
- Source videos and manifests live in the gitignored `.context/videos/<deck>/` of the working copy; they are not committed.
- MP4s remain in git history (no rewrite, per plan).
- Four Volume sources are low resolution (Shark Week 480×360, Murat Pak and Tylenol 640×360, HomeAdvisor 720×540).
