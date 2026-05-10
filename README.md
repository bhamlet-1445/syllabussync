# SyllabusSync
**AI-powered syllabus to calendar converter**

TAC 459 — Generative AI & NLP | Team G | USC Spring 2026

---

## Team
Bryce Hamlet · Jonathan Fisher · Ethan Say · Boyue Dong · Stefanie Akilian · Lauren Graham · William Jou

---

## What It Does
Students receive 4–5 syllabi every semester with inconsistent formatting and buried deadlines. **SyllabusSync** uses AI to automatically extract every assignment, exam, and deadline from a course syllabus into a clean, structured task list — then exports directly to Google Calendar, Apple Calendar, or CSV in one click.

---

## How to Run

### Step 1 — Get an API Key
1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign in → click **API Keys** → click **Create Key**
3. Copy the key (starts with `sk-ant-...`)

### Step 2 — Add Your API Key
1. Download `SyllabusSync.html`
2. Open it in any text editor, I would just edit in the GitHub and command F and replace with your own API Key.
3. On the first line of the `<script>` section, find:
   ```
   var API_KEY = 'YOUR-API-KEY-HERE';
   ```
4. Replace `YOUR-API-KEY-HERE` with your Anthropic API key
5. Save the file

### Step 3 — Run the App
1. Open `SyllabusSync.html` in **Google Chrome**
2. Upload a syllabus PDF or click **Paste Text** and paste syllabus content
3. Click **Extract with AI**
4. Review the extracted tasks
5. Export to **Google Calendar**, **Apple Calendar**, or **CSV**

> **Note:** The app requires an internet connection to call the Claude API.

---

## Features
- Upload PDF or paste syllabus text
- AI extracts every assignment, exam, quiz, project, and deadline
- Tasks labeled by type with color coding
- Export as `.ics` file (imports into Google Calendar, Apple Calendar, Outlook)
- Export as CSV for Notion or spreadsheets
- No sign-up or installation required — runs entirely in the browser

---

## NLP Pipeline

```
Syllabus Text → spaCy NLP → Regex Task Detection → Date Parsing → DataFrame → Calendar / CSV
```

| Component | Technique | Purpose |
|---|---|---|
| Date Extraction | spaCy NER + dateparser | Detect and normalize inconsistent date formats |
| Task Classification | Regex keyword matching | Label tasks as Exam, Assignment, Project, Reading, or Other |
| Data Cleaning | pandas | Remove duplicates, normalize task names |
| AI Extraction | Claude API (Anthropic) | High-accuracy extraction on messy real-world syllabi |

See `SyllabusSync_MVP.ipynb` for the full NLP pipeline demo — fully runnable in Google Colab, no setup needed.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| AI Extraction | Claude API (Anthropic) — claude-opus-4-5 |
| PDF Parsing | PDF.js |
| NLP Demo | Python, spaCy, dateparser, pandas |
| Calendar Export | iCalendar (.ics) standard format |

---

## File Structure

```
syllabussync/
├── SyllabusSync.html        # Main app — open in Chrome to run
├── SyllabusSync_MVP.ipynb   # NLP pipeline demo (Google Colab)
└── README.md
```

---

## Roadmap

**Phase 1 — MVP (complete)**
- [x] AI-powered task extraction
- [x] PDF upload and text paste
- [x] Editable task cards
- [x] CSV export
- [x] Google Calendar / Apple Calendar / Outlook export via .ics

**Phase 2 — Final MVP (complete)**
- [x] Deadline reminders and push notifications
- [x] Stats dashboard
- [x] Multi-Syllabus Upload
- [x] Print/Save as pdf view
- [x] Make Design more polished
