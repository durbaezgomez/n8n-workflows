# Slack AI Integration Workflow

## Workflow Overview

- **Trigger**:  
  Listens for specific messages in a Slack channel.  
  - Node: `Slack Trigger`.

- **Message Filtering**:  
  Checks if the message is from a specific user.  
  - Node: `Filter`.

- **AI Agent for Processing**:  
  Passes the Slack message to an AI agent for response generation.  
  - Node: `AI Agent`.  
  - Integrated with: `OpenRouter Model`.  

- **Memory Management**:  
  Utilizes a memory buffer to maintain context across interactions.  
  - Node: `Window Buffer Memory`.

- **Response Delivery**:  
  Sends the generated response back to the Slack channel.  
  - Node: `Slack`.

## Key Technologies

- **Slack**: API integration for triggering and sending messages.  
- **OpenAI (via OpenRouter)**: For AI-driven response generation.  
- **LangChain**: Manages AI processing and memory.  
- **n8n**: Workflow automation.  

## Purpose  
Creates an automated Slack bot to respond to user messages with context-aware AI-generated responses.  