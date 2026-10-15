# SoloDesk — your freelance back office

SoloDesk is a local-first mini workspace for freelancers. Track invoices and payment status, see earned/pending/overdue totals, export invoice records to CSV, and draft payment reminders or service descriptions with an open-weight model running through Ollama.

## Features
- Dashboard with paid, pending, overdue, and client totals
- Create, search, filter, delete, and CSV-export invoice records
- Local browser storage for invoice data (`localStorage`)
- AI tools for payment reminders, invoice service descriptions, and cleaning up rough notes
- Ollama integration through a small Node.js local server
- Template fallback if Ollama isn't installed or running
- Responsive layout for desktop and mobile

## Requirements
- Node.js 18 or newer
- Optional for real local AI: [Ollama](https://ollama.com/)

## Run the app
1. Extract this folder.
2. Open a terminal in the project directory.
3. Run `npm start`.
4. Open `http://127.0.0.1:3000` in your browser.

The core invoice tracker and AI template fallback work without Ollama.

## Enable open-weight AI locally
1. Install Ollama from https://ollama.com/.
2. In a terminal, download a model, for example: `ollama pull qwen2.5:3b`
3. Make sure Ollama is running.
4. Start SoloDesk with `npm start` and open the app again.

To use another Ollama model, set the `OLLAMA_MODEL` environment variable before starting the server.

Windows PowerShell:
```powershell
$env:OLLAMA_MODEL="qwen2.5:3b"
npm start
```

macOS/Linux:
```bash
OLLAMA_MODEL=qwen2.5:3b npm start
```

## Privacy and limitations
- Invoice records stay in this browser's local storage; this starter project does not have accounts, cloud sync, encryption-at-rest, or multi-device backup.
- When using the local model, prompts go to the local SoloDesk server and then to Ollama on the same computer. No hosted AI API is used by this app.
- Google Fonts is loaded from a CDN, so the interface may request font files online. For fully offline use, remove the `@import` line from `styles.css` and use system fonts.
- The fallback generator is a template, not an AI model. The UI labels which mode produced the draft.
- AI drafts may be inaccurate or inappropriate. Review all details before sending. This is not accounting, tax, or legal advice.
- Invoice data is stored per browser profile. Clearing site data may erase it. Export CSV backups regularly.

## Project structure
- `index.html` — app interface
- `styles.css` — responsive styling
- `app.js` — dashboard, invoice storage, CSV export, and AI tools
- `server.js` — local static server and Ollama bridge
- `package.json` — start command and project metadata

## Quick test checklist
- Add a paid invoice and confirm the earned total changes.
- Add a pending invoice with a past due date and confirm it appears as overdue.
- Search/filter invoices and export a CSV.
- Open AI assistant and generate a reminder with Ollama stopped; confirm template fallback is labelled.
- Start Ollama and run `ollama pull qwen2.5:3b`; generate again and confirm the output mode says Local open-weight model.
