# 🎓 CampusCopilot

CampusCopilot is an open-source, local-first Autonomous AI Agent built to solve the digital information overload faced by college students. 

Rather than acting as a passive email filter, CampusCopilot actively reads emails, parses complex attachments (PDFs/Excel), manages your Google Calendar and Tasks, and acts as a Career Co-Pilot to match incoming placement opportunities with your resume.

## ✨ Features
* **Bring-Your-Own-Credentials (BYOC):** Complete privacy. Runs locally on your machine using your own Google Cloud and LLM API keys.
* **Intelligent Parsing:** Uses `pandas` and `pdfplumber` to search through massive college spreadsheets and seating charts for your specific Registration Number.
* **Human-in-the-Loop:** Powered by LangGraph. If an assignment deadline is unclear, the agent pauses and asks you for clarification via the chat interface.
* **Career Co-Pilot:** Automatically compares incoming job alerts with your local resume, identifies skill gaps, and suggests real-time resume edits.
* **Adaptive Memory:** Learns your preferences over time and stores past emails in a local Vector Database (ChromaDB) for instant recall.

## 🛠 Tech Stack
* **Backend:** Python, FastAPI / LangGraph
* **AI & Logic:** Groq (Llama 3) / Google Gemini Flash, OpenAI Python SDK
* **Data Processing:** pandas, pdfplumber
* **Databases:** SQLite (Profile/State), ChromaDB (Vector Memory)
* **Integrations:** Google APIs (Gmail, Calendar, Tasks)

## 🚀 Getting Started
Check out the `instructions.md` file for a full step-by-step guide on setting up your local credentials and running the application.

## 🤝 Contributing
Contributions are welcome! Check out `tasks.md` to see what is currently in progress or open an issue to suggest a new feature.
