# Developer Setup & Instructions

To run this application locally, you will need to set up your own API credentials.

## Prerequisites
1. Python 3.10+ installed.
2. A Google Cloud account.
3. An API key from Groq or Google AI Studio.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/CampusCopilot.git
   cd CampusCopilot
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Google API Setup (BYOC)
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project named "CampusCopilot".
3. Enable the following APIs:
   - Gmail API
   - Google Calendar API
   - Google Tasks API
4. Go to **OAuth consent screen**, set user type to **External**, and add your email to "Test Users".
5. Go to **Credentials** -> Create Credentials -> **OAuth client ID** (Desktop App).
6. Download the JSON file, rename it to `credentials.json`, and place it in the root folder of this project.

## LLM API Setup
1. Create a `.env` file in the root directory.
2. Add your LLM API Key:
   ```env
   GROQ_API_KEY=your_api_key_here
   ```

## Running the App
1. Run the main application:
   ```bash
   python main.py  # Or streamlit run app.py
   ```
2. On the first run, a browser window will open asking you to authenticate with Google. Accept the permissions to generate your `token.json`.
