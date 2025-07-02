# AI-Powered README Generator for n8n Workflows

## Description
This n8n workflow automatically generates README files for your n8n workflows. 🚀 It analyzes the workflow JSON, extracts key information, and uses an AI agent to create a clear and concise README.md file.  This makes sharing and documenting your workflows super easy! ✨

## Used Nodes and Integrations
* **n8n Nodes:**
    * Execute Workflow Trigger
    * Code
    * Set
    * Manual Trigger
    * n8n
    * GitHub
* **External Integrations:**
    * GitHub
    * OpenRouter (using Google Gemini Pro)
    * Langchain

## Setup Instructions
1. **Workflow Setup:** Copy the workflow JSON and import it into your n8n instance. ✅
2. **Credentials:** Configure the necessary credentials for:
    * **n8n API:**  Allow the workflow to access and fetch workflow details.
    * **GitHub OAuth2 API:**  Provide access to your GitHub repository.
    * **OpenRouter API Key:**  Enable access to the OpenRouter Language Model.
3. **Parameters:**
    * **Workflow ID:** Specify the workflow ID as an input for lookup.
    * **GitHub Repository Details:** Update the values for Owner and Repository in GitHub nodes to match your target repo.
4. **JSON Filename:** The Set Node helps determine the name for the exported workflow content. Adjust if needed.
5. **AI Agent Prompt:** Fine-tune the prompt in the AI Agent node if you need specific information or formatting in the README.

🔧 Once you've completed these steps, you're ready to generate READMEs automatically! 🎉