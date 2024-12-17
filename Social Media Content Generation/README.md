## Social Media Post Automation Workflow  

### Workflow Summary  
- **Trigger**: Manual start for testing.  
- **Fetch Topics**: Retrieves data (topics, audience, instructions) from Google Sheets.  
- **AI Content Generation**: Generates platform-specific social media posts using OpenAI (via LangChain).  
- **Memory**: Uses LangChain memory to maintain context.  
- **Output Formatting**: Custom JavaScript formats AI responses.  
- **Update Sheets**: Writes generated content back to Google Sheets.  

### Technologies Used  
- **n8n Nodes**: Google Sheets, LangChain (AI & Memory), Code Node, Manual Trigger.  
- **Third-party Services**: OpenAI (via OpenRouter), Google Sheets API.  

### Purpose  
Automates social media content creation and organization for efficient workflow management.  

<img width="1100" alt="Zrzut ekranu 2024-12-17 o 14 08 23" src="https://github.com/user-attachments/assets/83a6cebc-6c22-4969-a50b-d8b73ba0c717" />
