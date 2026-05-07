# Yardi Project Setup Agent

## Project Overview
This is a browser-based Yardi Implementation documentation agent hosted on GitHub Pages.
GitHub repo: https://github.com/takala97/Yardi
Live URL: https://takala97.github.io/Yardi

## File Structure
- `index.html` — The main agent application (single file, all JS/CSS inside)
- `templates/` — BPR Word templates and RFI Excel template stored on GitHub

## Templates Folder (on GitHub at /templates/)
The following files must be in the GitHub `templates` folder:
- `01-_Business_Process_Requirement_-_Vendor_Cafe.docx.docx`
- `02-_Business_Process_Requirement_-_Procure_to_Pay.docx.docx`
- `03-._Business_Process_Requirement_-_FA.docx.docx`
- `04-._Business_Process_Requirement_-_Work_Orders.docx.docx`
- `05-_Business_Process_Requirement_-_Inspection_and_PPM.docx.docx`
- `RFI_Collection_Sheet.xlsx`
- `BPR_Agenda_Template.docx`

## Token System
Templates use these tokens which get replaced at generation time:
- `{{CLIENT_NAME}}` — Client company name
- `{{CONSULTANT_NAME}}` — Yardi consultant name(s)
- `{{SESSION_DATE}}` — BPR session date (per module)
- `{{WORKSHOP_OWNER}}` — Consultant assigned to that module
- `{{BPR_FROM}}` — BPR sessions start date
- `{{BPR_UNTIL}}` — BPR sessions end date

## How It Works
1. User fills in client details and selects modules in the browser form
2. Agent fetches real .docx/.xlsx templates from GitHub raw URLs
3. JSZip processes the files, replacing {{TOKEN}} placeholders
4. Completed files download directly to the user's browser

## Key Libraries (loaded via CDN)
- JSZip 3.10.1 — for opening and saving .docx files
- XLSX 0.18.5 — for Excel file generation

## What To Do When Asked To Make Changes
1. Edit `index.html` directly
2. Run `git add index.html && git commit -m "description" && git push`
3. The live GitHub Pages site updates within 30 seconds

## GitHub Config in index.html
```javascript
var GITHUB_USER   = "takala97";
var GITHUB_REPO   = "Yardi";
var GITHUB_BRANCH = "main";
```

## Current Phase
Phase 1 — Document generation:
- ✅ Cloud environment setup email (.docx)
- ✅ BPR Agenda (.docx) — per module dates/times/attendees
- ✅ BPR Documents per module (.docx) — from real templates
- ✅ RFI Collection Sheet (.xlsx)
