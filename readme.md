# 🤖 Multi-Modal Telegram AI Assistant & YouTube Summarizer
*(Role: Automation Engineer & AI Integrator)*

---

## 💡 The Problem
Relying on commercial cloud AI services (like ChatGPT) for daily tasks, web research, and video summarization requires expensive subscriptions and compromises personal data privacy. Furthermore, standard AI chatbots cannot natively "watch" YouTube videos or look up real-time facts without complex plugins. Users need a centralized, private, and highly capable digital assistant accessible directly from their mobile devices (via Telegram) that can handle both conversational memory and active web-research tasks without leaking data to the cloud.

## 🎯 The Solution
I engineered a fully autonomous, self-hosted AI assistant using n8n and Telegram. The system features an intelligent router that analyzes incoming messages. Standard questions are routed to a LangChain-powered AI Agent equipped with conversational memory and a Wikipedia search tool, allowing it to autonomously research facts. If a YouTube link is detected, the system dynamically extracts the video ID, fetches the WEBVTT transcript via an external API, and passes the entire transcript to a local LLaMA 3.1 model for deep summarization. The entire cognitive engine runs locally via LM Studio, ensuring zero data leakage and zero API costs.

---

## 🛠️ The Tech Stack
* **Automation Platform:** n8n (Node.js)
* **AI / ML:** LLaMA 3.1 8B Instruct, LM Studio (Local Offline Inference)
* **Integrations:** Telegram Bot API, Wikipedia Tool, RapidAPI (YouTube Transcripts)
* **Techniques:** Agentic Function Calling, RegEx Data Extraction, Advanced Routing

---

## 🏗️ Engineering & Architecture Highlights

### 1. Intelligent Multi-Path Routing
Designed an event-driven n8n workflow utilizing a Switch node to intelligently route incoming Telegram messages. By applying regex pattern matching, the system automatically detects YouTube URLs (`youtube.com` or `youtu.be`) and diverts them to a specialized transcript-processing pipeline, while sending normal conversational messages to the primary AI Agent.

### 2. Autonomous Function Calling & Web Research
Implemented an Advanced AI Agent utilizing LangChain nodes. Instead of relying on static knowledge, the LLaMA 3.1 model is equipped with a Wikipedia tool. The model autonomously determines when a user's question requires external knowledge, triggers the tool, reads the search results, and synthesizes a final, factually accurate answer.

### 3. Dynamic API Integration & RegEx Extraction
Engineered a seamless pipeline to bypass YouTube's lack of native transcript APIs. The workflow uses Javascript Regular Expressions (`/[a-zA-Z0-9_-]{11}/`) to dynamically extract the precise 11-character Video ID from any variation of a YouTube URL. This ID is then injected into an HTTP Request node to fetch WEBVTT formatted captions from a 3rd-party RapidAPI service.

### 4. Local AI Inference & Zero-Data-Leakage
Integrated the entire automation framework with a local LM Studio instance hosting the newly released, highly capable LLaMA 3.1 8B model. By proxying the standard OpenAI connection nodes to a `localhost` endpoint, the system performs complex natural language processing, tool calling, and massive document summarization entirely offline.

---
