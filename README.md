# youtube-discord-notifier

Polls the YouTube RSS feed every 15 minutes and posts new uploads to a Discord channel via webhook.

**No API keys required** — uses YouTube's public RSS feed.

## How it works

1. GitHub Actions runs on a 15-minute schedule
2. Fetches `https://www.youtube.com/feeds/videos.xml?channel_id=UC4_toGdH1h8QMd5w9eCnWdw`
3. Compares the latest video ID to `vars.LAST_VIDEO_ID` (stored as a repo variable)
4. If new, posts a Discord embed to `#new-videos` and updates the stored ID

## Setup

Add one secret in **Settings → Secrets and variables → Actions → Secrets**:

| Name | Value |
|---|---|
| `DISCORD_WEBHOOK` | The webhook URL for `#new-videos` |

The `LAST_VIDEO_ID` variable is managed automatically by the workflow.
