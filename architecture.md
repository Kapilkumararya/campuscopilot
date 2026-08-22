# System Architecture

## Data Flow
1. **Ingestion:** Gmail API polls for new emails -> Saves to `temp_storage/`.
2. **Parsing:** `pdfplumber` & `pandas` scan attachments for user Identifiers (from SQLite).
3. **Triage (LLM):** Email body + Extracted Attachment Data -> LLM Router -> Outputs JSON Intent.
4. **State Management (LangGraph):**
   - High Confidence -> Execute API Call (Calendar/Tasks).
   - Low Confidence -> Trigger `interrupt_before` -> Push prompt to Frontend.
5. **Execution:** Update Google Workspace & insert embeddings into ChromaDB.
6. **Career Branch:** If `PLACEMENT_ALERT` -> Load User Resume -> LLM Gap Analysis -> Chatbot suggestion.

## Database Schemas (SQLite)
* **User Profile:** `user_id`, `name`, `reg_no`, `major`
* **Aliases/Identifiers:** `id`, `user_id`, `search_string` (e.g., "21BCE1234", "kapil.k@college.edu")
* **Preferences:** `id`, `user_id`, `preference_text`
