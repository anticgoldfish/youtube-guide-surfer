# YouTube Guide v1.1.5 — New-repository edition

A GitHub Pages live-TV guide for YouTube, configured for `anticgoldfish/youtube-guide-surfer`.

- **Add Channel** (no PIN), with GitHub PAT and YouTube Data API key saved locally in the browser.
- Creating a channel attempts to publish immediately to the shared `YouTube-Guide/channels.json`.
- An included GitHub Actions workflow checks roughly every 30 minutes and replenishes 100-hour channel schedules, with reruns as a fallback. Set the GitHub Actions `YOUTUBE_API_KEY` secret to enable unattended new-video discovery.
- Public channel metadata and UTC timestamps remain suitable for a future Android TV APK.
- **This fresh-install ZIP contains an empty `YouTube-Guide/channels.json`.** If moving channels from an existing repository, replace this blank file with a backup of the old channel library **before** the first upload.
- No API keys or personal access tokens are bundled.

See `GITHUB-SETUP.md` for the full installation steps and `TV-APP-DATA-CONTRACT.md` for the read-only program schedule format.
