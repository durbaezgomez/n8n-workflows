
# Save Workflow To GitHub

## Description
This workflow automates the process of saving an n8n workflow to a GitHub repository. It retrieves the workflow data, generates a README file using an AI agent, and then either creates or updates the workflow's JSON file and corresponding README in the repository.

 🚀 This allows for easy version control and sharing of n8n workflows.

## Used Nodes and Integrations

- **n8n Nodes:**
    - Execute Workflow Trigger
    - Code
    - Set
    - Manual Trigger
    - n8n
    - Sticky Note
- **Langchain Nodes:**
   - AI Agent
   - Openrouter (LLM Chat)
- **GitHub Node**

## Setup Instructions

To use this workflow, you'll need to configure a few things:

1.  **n8n API Credentials:** ✅ Configure the n8n API credential to allow access to the workflow you want to save from the list.  You will also need to select the correct workflow from **Get Workflow From List**

2.  **GitHub OAuth2 Credentials:** ✅ Configure the GitHub OAuth2 API credential to enable interaction with your GitHub repository.

3.  **GitHub Repository:**  Make sure you set your desired user and repository to where the workflows will be saved. 

4. **OpenRouter API Key**: Make sure you have an OpenRouter account and an API Key to be able to use the AI Agent.

5.  **Workflow Trigger:** ✅ By default the workflow can be triggered manually from the n8n panel or by calling another workflow that passes its ID.

Once these steps are completed, you should be able to effectively save your n8n workflows to GitHub  🚀
