# 🎯 n8n Lead Management System

> Automated lead capture and distribution system — 
> logs to Google Sheets, alerts on Slack, creates 
> Notion CRM records in real-time.

<img width="1156" height="464" alt="image" src="https://github.com/user-attachments/assets/8f40b297-42e8-4b01-b721-4a8e7517192b" />


---

## 🚀 What It Does

When a lead submits a form, this workflow automatically:

- 📊 **Logs to Google Sheets** — permanent lead database
- 💬 **Alerts team on Slack** — real-time sales notification
- 📝 **Creates Notion record** — CRM entry with full details
- ⚡ **All in under 2 seconds** — zero manual work required

---

## 🔄 Workflow Architecture
POST /webhook
│
▼
┌─────────────────┐
│  Google Sheets  │ ← Append lead row
└────────┬────────┘
│
▼
┌─────────────────┐
│      Slack      │ ← Alert #new-channel
└────────┬────────┘
│
▼
┌─────────────────┐
│     Notion      │ ← Create CRM record
└─────────────────┘

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation engine |
| **Google Sheets** | Lead database |
| **Slack** | Real-time team alerts |
| **Notion** | CRM and lead tracking |

---

## 📸 Screenshots

### Workflow Canvas
![Canvas](screenshots/canvas.png)

### Google Sheets — 20+ Live Leads
![Sheets](screenshots/sheets.png)

### Slack — Real-time Alerts
![Slack](screenshots/slack.png)

### Notion — CRM Database
![Notion](screenshots/notion.png)

---

## 📥 API Input Format

Send a `POST` request to the webhook URL:

```json
{
  "name": "Ahmed Raza",
  "email": "ahmed@company.com",
  "company": "TechPK",
  "phone": "+92-300-1234567",
  "source": "LinkedIn"
}
```

### Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| name | string | ✅ | Full name of lead |
| email | string | ✅ | Email address |
| company | string | ✅ | Company name |
| phone | string | ✅ | Phone number |
| source | string | ✅ | Where lead came from |

---

## ⚙️ Setup Instructions

### Prerequisites
- n8n account (cloud or self-hosted)
- Google account
- Slack workspace
- Notion account

### Step 1 — Import workflow
1. Download `workflow.json`
2. Open n8n → click **"Import"**
3. Select the JSON file

### Step 2 — Connect credentials
Connect these in n8n Settings → Credentials:
- ✅ Google Sheets OAuth2
- ✅ Slack OAuth2
- ✅ Notion OAuth2

### Step 3 — Set up Google Sheets
Create a sheet with these headers in Row 1:
name | email | company | phone | source | created_at

### Step 4 — Set up Notion database
Create a database with these properties:
Name (Title) | Email (Text) | Company (Text) |
Phone (Text) | Source (Text) | Created At (Date)

### Step 5 — Connect Notion integration
1. Go to notion.so → Settings → Connections
2. Create new integration
3. Share your Leads database with the integration

### Step 6 — Activate
Toggle workflow to **Active** in n8n → copy Production URL → done!

---

## 📊 Performance

- ✅ Tested with **20+ leads** in live environment
- ✅ Processing time: **under 2 seconds** per lead
- ✅ **3 platforms** updated simultaneously
- ✅ **24/7 uptime** on production webhook
- ✅ Zero manual intervention required

---

## 🔐 Security

For production use, add webhook authentication:

1. Open Webhook node in n8n
2. Set **Authentication** to Header Auth
3. Add header: `X-API-Key: your-secret-key`
4. Include this header in all requests

---
