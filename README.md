✈️ AeroIQ: Autonomous Flight Search AI Agent
====================================================================

AeroIQ is a production-grade conversational AI agent designed to extract complex travel intents from unstructured natural language and orchestrate live flight lookups. Built using n8n, LangChain, and Google Gemini, this agent enforces strict output requirements, handles stateful conversations, and manages multi-channel ingestion.

🚀 Live Deployments (⬇️⬇️You Can Access the AI Agent Here⬇️⬇️)
-------------------
* Web Interface: https://aeroiq.vercel.app
* Telegram Bot: @SkyMind01_bot (https://t.me/SkyMind01_bot)


🏗️ System Architecture
-------------------
The workflow relies on an advanced event-driven orchestration pipeline:

* Multi-Channel Input Matrix: Ingests concurrent user requests via native Telegram Webhooks and n8n Web Chat Triggers to service both frontends seamlessly.

* LangChain Orchestration: Utilizes a LangChain Agent framework paired with an aggressive prompt engineering guardrail system. The agent strictly parses dynamic parameters (e.g., relative dates like "next Friday", one-way vs. round-trip isolation, passenger counts) before executing external tool calls.

* Deterministic Fallback Routing: Designed for high availability, the primary model (gemini-3-flash-preview) is backed by a secondary fallback model (gemini-3.1-flash-lite-preview). The node evaluates up to 5 retries with a 5000ms delay to gracefully handle rate limits.

* Stateful Session Memory: Employs a context window buffer memory (capacity of 4 messages) tied to unique Telegram Chat IDs and Web Session IDs to maintain conversational context.

* Live API Tooling & Output Normalization: Connects directly to the SerpAPI Google Flights engine. Instead of relying on the LLM for unstable payload formatting, raw tool responses bypass the model and route into a custom JavaScript sanitation layer. This code strips rogue markdown, executes 4,000-character payload truncation, and reformats pricing into the Indian en-IN numbering standard.


🛠️ Tech Stack
----------
* Automation & Orchestration: n8n, LangChain
* Large Language Models: Google Gemini 3 Flash (Preview), Gemini 3.1 Flash Lite
* External APIs: SerpAPI (Google Flights), Telegram Bot API
* Scripting: Custom JavaScript (Payload parsing, regex stripping)


📥 Installation & Setup
--------------------
1. Clone this repository.
2. Open your self-hosted or cloud n8n instance.
3. Select "Import from File" and upload "✈️ AeroIQ Flight Search AI Agent.json".
4. Connect your Google Gemini API, Telegram Bot Token, and SerpAPI Key to the respective credential blocks.
5. Activate the workflow.

Developed by: Shayaan Patel
