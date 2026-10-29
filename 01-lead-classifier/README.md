# 01 · Lead Classifier

## The business problem

Small businesses receive leads through forms and messages, and someone has to read each one to decide which deserve a quick reply. Hot leads get lost among the rest, and response time suffers.

## The solution

An n8n workflow that receives each new lead, uses a local AI model to classify it as **HOT, WARM or COLD**, saves the result in Google Sheets, and sends an instant Telegram alert when the lead is HOT.

> The system works with **Spanish-language messages**.

## How it works

1. **Webhook** receives the lead.
2. **AI Agent** (Ollama, llama3.1) classifies it and returns structured JSON.
3. **Edit Fields** prepares the data.
4. **Google Sheets** stores the lead and its classification.
5. **IF** checks whether the lead is HOT.
6. **Telegram** sends an alert to the team if it is.

## Stack

n8n · Ollama (llama3.1) · Docker · Google Sheets · Telegram

## Problems I solved

- **Slow first run:** the local model takes 1-2 minutes to load into memory after days without use. I learned to expect it and warm up the model before testing.
- **Expiring Google permissions:** while the Google Cloud app is in testing mode, access expires every 7 days. I fixed it by re-authorizing the credential.
- **Wrong timestamps:** I set the timezone in each workflow's settings so dates match the local time.

## Files

- `workflow.json`: coming soon
- `screenshots/`: coming soon
