# Proposed Solution: CampusCopilot

## Overview
**CampusCopilot** is an open-source, local-first Autonomous AI Agent specifically designed for college students. It acts as a digital administrative assistant and career co-pilot, intelligently managing communications, extracting actionable data, and directly integrating with productivity tools.

## Core Pillars of the Solution

### 1. The Bring-Your-Own-Credentials (BYOC) Model
To ensure maximum privacy and bypass expensive third-party security audits (like Google CASA), the application runs locally. Users provide their own Google Cloud `credentials.json` and a free LLM API key (e.g., Groq, Google AI Studio).

### 2. Autonomous Triage & Execution
The system securely reads incoming emails, categorizes them by intent (e.g., `PLACEMENT_ALERT`, `ASSIGNMENT_DEADLINE`), and autonomously interacts with the Google Calendar and Google Tasks APIs to organize the student's schedule.

### 3. Deep Attachment Parsing
Instead of just reading subject lines, the agent actively downloads attachments. It uses `pandas` (for spreadsheets) and `pdfplumber` (for PDFs) to scan for the user's specific identifiers (like Registration Number or Name), extracting exactly what is relevant to them.

### 4. Interactive State Management (Human-in-the-Loop)
Powered by **LangGraph**, the agent isn't a black box. If an email's instructions are ambiguous, the agent pauses its automated workflow and sends a message to the user via the Dashboard Chatbot to ask for clarification before creating a calendar event.

### 5. Career Co-Pilot & Adaptive Memory
The system maintains a local SQLite database for the user's dynamic profile and a Vector Database (ChromaDB/FAISS) for long-term email memory. When placement opportunities arrive, the agent cross-references the job requirements with the student's resume, suggests targeted edits, and updates user preferences based on chat interactions.
