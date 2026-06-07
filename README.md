# n8n AI News Workflow

Automated daily email digest with the latest AI news from TechCrunch, delivered every night at 11:45 PM via Gmail.

## What it does

1. **Schedule Trigger** — fires every day at 11:45 PM
2. **Fetch RSS Feed** — pulls the latest articles from TechCrunch's AI category
3. **Format HTML Email** — extracts the top 6 articles and builds a clean, styled HTML email
4. **Send via Gmail** — delivers the digest to the configured recipient

## Nodes

| Node | Type | Purpose |
|------|------|---------|
| Every day at 11:45 PM | Schedule Trigger | Cron trigger (`45 23 * * *`) |
| RSS TechCrunch AI | HTTP Request | Fetches the RSS/XML feed |
| Format Email HTML | Code (JS) | Parses XML and builds HTML email |
| Send via Gmail | Gmail | Sends the formatted email |

## Setup

### 1. Gmail credential
- Go to **Settings → Credentials → Add credential → Gmail OAuth2**
- Complete the OAuth flow with the Gmail account you want to send from
- In the `Send via Gmail` node, select that credential

### 2. Recipient email
- In the `Send via Gmail` node, set the **To** field to the destination email address
- The workflow uses `$vars.RECIPIENT_EMAIL` — you can set this as an n8n variable or replace it directly with an email address

### 3. Schedule
- Default: every day at **11:45 PM** (cron `45 23 * * *`)
- Adjust the cron expression in the `Every day at 11:45 PM` node to change the time

### 4. Activate
- Toggle the workflow to **Active** in the top-right of the n8n editor

## Customization

- **Change the source**: Replace the RSS URL in `RSS TechCrunch AI` with any other RSS feed
- **Number of articles**: Change `itemBlocks.length < 6` in the Code node to show more or fewer articles
- **Email style**: Edit the HTML/CSS inside the Code node to match your brand colors
- **Send time**: Update the cron expression to any schedule you need

## Requirements

- n8n instance (self-hosted or cloud)
- Gmail account with OAuth2 credentials configured in n8n
