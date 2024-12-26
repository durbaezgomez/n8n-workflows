json
{
  "action": "Final Answer",
  "action_input": "
# Save Workflow To GitHub\n\n## Description\nThis workflow automatically generates a README.md file and a JSON file for a given n8n workflow and saves them to a GitHub repository. It fetches the workflow data using the n8n API, formats it, uses an AI agent to create the README content, and then pushes the files to a specified GitHub repository.  🚀\n\n## Used Nodes and Integrations\n*   **n8n Nodes:**
    *   Execute Workflow Trigger
    *   Code
    *   Set
    *   Manual Trigger
    *   n8n
    *   Sticky Note
*   **Langchain Nodes:**
    *   AI Agent
    *   LM Chat Open AI (OpenRouter)
*   **Integrations:**
    *   GitHub 🔑
    *   n8n API 🔑
    *   OpenRouter 🔑\n\n## Setup Instructions\n1.  **Credentials:** ✅
    *   Make sure you have configured the **n8n API** credentials.  You'll need the API key from your n8n instance. 🗝️
    *   Configure the **GitHub OAuth2 credentials** to connect to your GitHub repository. 🔑
    *   Set up the **OpenRouter API credentials** to use the AI Agent.
2.  **Trigger:** ✅
   * The workflow can be triggered manually by clicking on `Test Workflow` button or it can start after the execution of another workflow.\n3.  **GitHub Repository:** ✅
    *   Ensure that the `owner` and `repository` in the GitHub nodes match your GitHub account and the repository name where you want to save your workflows json and readme files.
4.  **OpenRouter Model:** ✅
    *   The workflow is using `google/gemini-2.0-flash-exp:free` model, ensure that this model is available, and you have set up the OpenRouter credential.
5.  **Workflow ID:** ✅\n    *  When triggered from another workflow the workflow ID is obtained from the event, if triggered manually the workflow fetches the latest workflow from a workflow list.\n\n**Important:** The workflow will create or update the required files into the root directory of your repository named with the name of your n8n workflow. 📁
"
}
