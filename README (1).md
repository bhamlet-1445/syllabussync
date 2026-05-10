# SyllabusSync
**AI-powered syllabus to calendar converter**

TAC 459 — Generative AI & NLP | Team G | USC Spring 2026

---

## Team
Bryce Hamlet · Jonathan Fisher · Ethan Say · Boyue Dong · Stefanie Akilian · Lauren Graham · William Jou

---

## What It Does
Students receive 4–5 syllabi every semester with inconsistent formatting and buried deadlines. **SyllabusSync** uses Claude AI to automatically extract every assignment, exam, and deadline from a course syllabus into a clean, structured task list — then exports directly to Google Calendar, Apple Calendar, or CSV in one click.

---

## How to Run

### Step 1 — Get an API Key
1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign in → click **API Keys** → click **Create Key**
3. Copy the key (starts with `sk-ant-...`)

### Step 2 — Add Your API Key
1. Download `SyllabusSync.html`
2. Open in any text editor (VS Code recommended)
3. Find on line 1 of the `<script>` section:
   ```
   var API_KEY = 'YOUR-API-KEY-HERE';
   ```
4. Replace `YOUR-API-KEY-HERE` with your Anthropic API key
5. Save the file

### Step 3 — Run the App
1. Open `SyllabusSync.html` in **Google Chrome**
2. Upload a syllabus PDF or click **Paste Text** and paste syllabus content
3. Click **Extract with AI**
4. Review, edit, and filter the extracted tasks
5. Export to **Google Calendar**, **Apple Calendar**, or **CSV**

> The app requires an internet connection to call the Claude API.

---

## Features

### Completed — v3 Final
- [x] Upload PDF or paste syllabus text
- [x] AI extraction using Claude API (claude-opus-4-5)
- [x] Stats dashboard — Total Tasks, Overdue, Due This Week, Upcoming
- [x] Due date countdown on every task ("Due in 3 days", "Overdue 2d", "Due today!")
- [x] Color-coded urgency (green / yellow / red)
- [x] Inline edit every task — name, date, type, points
- [x] Delete individual tasks
- [x] Add tasks manually
- [x] Filter by task type (All, Exam, Assignment, Project, Quiz, Reading, Other)
- [x] Sort by date, type, or name
- [x] Export as .ics file (Google Calendar, Apple Calendar, Outlook)
- [x] 24-hour reminder alarms embedded in .ics events
- [x] Export as CSV (includes Days Until Due column)
- [x] Print / Save as PDF view with clean print stylesheet
- [x] Sample syllabus for one-click demo
- [x] Full team credit in UI
- [x] Public GitHub repository with clean, runnable code
- [x] NLP pipeline Jupyter notebook (Google Colab ready)

### Phase 2 — Roadmap
- [ ] Google Calendar OAuth — push events directly without .ics download
- [ ] Notion integration
- [ ] Deadline push notifications
- [ ] Multi-course dashboard
- [ ] Syllabus change detection

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

See `SyllabusSync_MVP.ipynb` for the full pipeline demo — runnable in Google Colab, no setup needed.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| AI Extraction | Claude API (Anthropic) — claude-opus-4-5 |
| PDF Parsing | PDF.js (Cloudflare CDN) |
| NLP Demo | Python, spaCy, dateparser, pandas |
| Calendar Export | iCalendar (.ics) — RFC 5545 standard |

---

## File Structure

```
syllabussync/
├── SyllabusSync.html        # Main app — open in Chrome to run
├── SyllabusSync_MVP.ipynb   # NLP pipeline demo (Google Colab)
└── README.md
```
