# 🤖 Telegram AI Assistant & YouTube Summarizer

A multi-modal n8n automation workflow that acts as a personal AI assistant on Telegram. It features conversational memory, Wikipedia web research, and a dedicated pipeline for extracting and summarizing YouTube video transcripts using local LLMs.

## 📂 Repository Structure
*   `The AI Agent with Memory.json` - The exported n8n workflow file.

## 🛠️ Setup Instructions

### 1. Prerequisites
- n8n installed locally or cloud-hosted
- A running instance of LM Studio with Llama 3.1 8B Instruct model (running on port `1234`)
- A Telegram Bot Token (from BotFather)
- A RapidAPI key for the YouTube transcript API (optional, for video summaries)

### 2. Importing the Workflow
1. Open your n8n workspace.
2. Create a new workflow.
3. Click the menu in the top right and select **Import from File**.
4. Select the `The AI Agent with Memory.json` file from this repository.

### 3. Configuring Credentials
Once imported, you will need to update the credentials on several nodes:
1. **Telegram Trigger / Telegram Sender:** Create a new credential and paste your Telegram Bot Token.
2. **OpenAI Chat Model (LM Studio):** Double-click the OpenAI model node. Ensure the Base URL is set to `http://localhost:1234/v1` and use any placeholder string (e.g., `lm-studio`) for the API key.
3. **HTTP Request (YouTube Transcript):** Update the Header Auth credential with your RapidAPI key if you wish to use the YouTube summarization feature.

### 4. Activation
Toggle the workflow to **Active** in the top right corner. You can now chat with your assistant directly in Telegram!
