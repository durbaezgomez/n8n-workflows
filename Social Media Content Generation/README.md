## Social Media Post Automation Workflow  

<img width="763" alt="Zrzut ekranu 2024-12-23 o 13 06 59" src="https://github.com/user-attachments/assets/5327f63b-99e3-4cee-9836-243a0db909e3" />

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
