# Slack AI Assistant Workflow

This workflow integrates Slack with various AI and automation tools, leveraging n8n for seamless communication and task automation.

<img width="935" alt="Zrzut ekranu 2024-12-23 o 13 11 45" src="https://github.com/user-attachments/assets/33a10dc7-8ab3-4f3a-8488-eaae687fa036" />

## Features
- **Slack Integration**: Triggers on Slack messages and filters based on user or channel-specific criteria.
- **AI-Powered Assistance**: Utilizes LangChain and OpenAI's GPT models for advanced language processing and task handling.
- **Dynamic Tools**: Includes Wikipedia search, calculations, and web search using SerpAPI.
- **Google Integration**: Accesses Google Drive, Sheets, and Calendar to manage data and create events directly.
- **Sub-Workflow for Calendar Data**: Uses a sub-workflow to extract, format, and validate calendar event details before scheduling.
- **Stateful AI**: Employs memory to maintain conversation context for enhanced interactivity.

## Workflow Overview
1. **Trigger**: Listens to messages in a specified Slack channel.
2. **Filter**: Ensures only specific users or conditions trigger further actions.
3. **AI Processing**: Handles requests with OpenAI's GPT and LangChain agents.
4. **Tool Access**:
   - Wikipedia and SerpAPI for real-time information.
   - Google Drive and Sheets for data retrieval.
   - **Sub-Workflow**: Calls a dedicated workflow to process calendar event data for Google Calendar.
5. **Response**: Outputs processed results back to Slack in real time.

## Requirements
- Slack API credentials.
- OpenAI API key (via OpenRouter).
- Google Workspace API credentials.
- SerpAPI key (for web search functionality).

## Use Cases
- Real-time Q&A or task automation in Slack.
- Simplified scheduling with robust calendar event processing.
- Context-aware information retrieval and processing.

This workflow showcases practical AI-powered automation with n8n, highlighting the ability to connect multiple services and leverage sub-workflows for modular, efficient task handling.
