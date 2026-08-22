# CampusCopilot: Development Roadmap & Learning Guide

This roadmap is designed to guide you from building the Minimum Viable Product (MVP) to a fully autonomous AI agent. It follows a "Learn -> Build" cycle.

---

## Phase 1: The Foundation (The MVP)
**Goal:** Authenticate, fetch emails, and store attachments locally.

* **What to Learn:**
  * OAuth 2.0 flow for Desktop Applications.
  * Google API Python Client (`google-api-python-client`).
  * Basic File I/O in Python.
* **What to Build:**
  * Implement the Google Cloud login script (`auth.py`) to generate `token.json`.
  * Write the polling script (`mvp_fetcher.py`) that uses `last_run.txt` to only fetch new emails.
  * Save plain text email bodies and attachments to a `temp_storage/` folder.

---

## Phase 2: Attachment Intelligence
**Goal:** Automatically scan downloaded files for the student's Registration Number.

* **What to Learn:**
  * `pandas` library basics: Reading `.xlsx`/`.csv` files, filtering rows, and string matching.
  * `pdfplumber` library basics: Extracting tables and text from PDFs.
* **What to Build:**
  * Create an `extractor.py` module.
  * Add logic to open saved Excel/PDF files, search for identifiers (e.g., "21BCE..."), and extract the matching row/paragraph.

---

## Phase 3: The LLM Brain & Triage
**Goal:** Give the system the ability to understand context and categorize emails.

* **What to Learn:**
  * How to use the `openai` Python SDK with Groq or Google AI Studio.
  * Prompt Engineering: Forcing Structured Output (JSON mode).
* **What to Build:**
  * Build the LLM Router. Pass the email text and extracted attachment rows to the LLM.
  * Force the LLM to return a JSON object categorizing the email (`type: PLACEMENT`, `urgency: HIGH`).

---

## Phase 4: Autonomous Actions & Google APIs
**Goal:** Let the agent manage your calendar and tasks.

* **What to Learn:**
  * Google Calendar API: Creating events and parsing dates.
  * Google Tasks API: Creating task lists and to-do items.
* **What to Build:**
  * Write execution functions: `create_calendar_event()` and `add_to_tasks()`.
  * Connect the LLM Router's output to these functions.

---

## Phase 5: Human-in-the-Loop & LangGraph
**Goal:** Make the agent pause when confused and ask the user for help.

* **What to Learn:**
  * `LangGraph`: State management, Nodes, Edges, and Interrupts (`interrupt_before`).
* **What to Build:**
  * Refactor the procedural pipeline into a LangGraph workflow.
  * Implement the confidence scoring node.
  * Create the pause/resume mechanism for user clarification.

---

## Phase 6: The Career Co-Pilot
**Goal:** Compare job descriptions to the user's resume and suggest edits.

* **What to Learn:**
  * Reading and manipulating document files (`python-docx` or PyPDF).
  * Advanced LLM comparisons (Skill gap analysis).
* **What to Build:**
  * A LangGraph branch that triggers on `PLACEMENT_ALERT`.
  * Logic to pull the user's resume, compare it to the email, and output a JSON of missing skills and suggested resume edits.

---

## Phase 7: The Dashboard (UI/UX)
**Goal:** Bring it all together in a beautiful, unified interface.

* **What to Learn:**
  * `Streamlit` or `FastAPI` (backend) + `Next.js`/`React` (frontend).
* **What to Build:**
  * An overview screen showing recent tasks and calendar events.
  * A chat interface connected to your LangGraph state so the agent can chat with the user, ask for clarification, and update the SQLite profile.
