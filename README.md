# Claude_Ai_2.0-n8n
# Manickam's N8N Project For Sysway Tech
live link :https://claude-ui-for-vercel-hosting.vercel.app/

WEB HOOK:http://localhost:5678/webhook/claude-chat



![alt](./Screenshot%202026-03-28%20154003.png)


A fully functional AI-powered chat module built with n8n workflow automation and a beautiful custom HTML/CSS/JS frontend.

## Files
![alt](./Screenshot%202026-03-28%20150848.png)

- `claude_chat_ui.html` — Frontend chat interface
- `claude_chat_n8n_workflow.json` — n8n backend workflow for Claude
- `gemini_chat_ui.html` — Frontend chat interface for Gemini
- `gemini_chat_n8n_workflow.json` — n8n backend workflow for Gemini

## n8n Workflow Nodes
![alt](./Screenshot%202026-03-28%20143756.png)


| Node | Purpose |
|---|---|
| Chat Webhook | Receives POST requests from the frontend |
| Parse Input | Extracts message and history |
| Claude / Gemini API | Calls the AI API |
| Format Response | Extracts reply text |
| Send Response | Returns JSON reply to frontend |
| Error Response | Handles errors gracefully |

## Setup

### Step 1 — Run n8n

```bash
npx n8n
```

Open `http://localhost:5678`

### Step 2 — Import Workflow

1. Open n8n
2. Click `+` New workflow
3. Click `...` menu → Import from file
4. Select `claude_chat_n8n_workflow.json` or `gemini_chat_n8n_workflow.json`

### Step 3 — Add API Key

**For Claude:**
1. Click the Claude API node
2. Add Header → Name: `x-api-key` → Value: `sk-ant-your-key`
3. Get key from: https://console.anthropic.com

**For Gemini:**
1. Click the Gemini API node
2. In the URL replace `YOUR_KEY_HERE` with your key
3. Get key from: https://aistudio.google.com/apikey

### Step 4 — Activate Workflow

Toggle the workflow to **Active** in n8n

### Step 5 — Open Chat UI

1. Open `claude_chat_ui.html` in your browser
2. Paste your webhook URL in the field at the bottom
3. Start chatting!

## Webhook URLs

```
POST http://localhost:5678/webhook-test/claude-chat
POST http://localhost:5678/webhook-test/gemini-chat
```

## Request Body (Postman / Frontend)

```json
{
  "message": "Hello! How are you?",
  "history": []
}
```

## Response

```json
{
  "reply": "Hello! How can I assist you today?",
  "model": "claude-sonnet-4-20250514",
  "timestamp": "2026-03-28T10:00:00.000Z"
}
```

## Tech Stack

- Frontend: HTML, CSS, JavaScript
- Backend: n8n (self-hosted)
- AI: Claude (Anthropic) / Gemini (Google)
- Communication: REST API / Webhook

## Cost

| API | Free? |
|---|---|
| Claude | $5 min top-up |
| Gemini | Free — 1500 req/day |
| Ollama | 100% free (local) |
