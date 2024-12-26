
# Save Workflow To GitHub

## Description
This workflow automates the process of saving an n8n workflow to a GitHub repository. It fetches the workflow data, formats it, generates a README file using an AI agent, and then either creates or updates both the workflow's JSON file and its README in a specified GitHub repository. 🚀

<img width="1243" alt="Zrzut ekranu 2024-12-26 o 15 36 11" src="https://github.com/user-attachments/assets/30893b07-03f3-4b97-854d-35c1ba39646c" />

## Used Nodes and Integrations

**Nodes:**

*   Execute Workflow Trigger
*   Code
*   AI Agent
*   Openrouter (LLM Chat Open AI)
*   GitHub
*   Set
*   Manual Trigger
*   n8n
*   Sticky Note

**Integrations:**

*   GitHub
*   OpenRouter API

## Setup Instructions

Before using this workflow, you'll need to configure the following:

1.  **GitHub OAuth2 Credentials:** ✅
    *   Make sure you have your GitHub OAuth2 credentials set up in n8n and selected in all of the GitHub nodes.
2.  **OpenRouter API Key:** ✅
    *   Ensure your OpenRouter API key is configured correctly within the 'Openrouter' node (it uses the credential named 'OpenRouter Credential').

3. **n8n API Credentials:** ✅
    *   Make sure you have your n8n API credentials set up in n8n and selected in both of the n8n nodes.

4.  **Repository and Owner:**
	* Inside the GitHub nodes, ensure the `owner` and `repository` are correctly set to target your desired GitHub repo. 🔧

5. **Manual Trigger vs Workflow Execution:**
	* The workflow has two starting points, it can either be executed manually using the 'When clicking ‘Test workflow’ node, or by passing the ID from the 'Execute Workflow Trigger'. 🕹️

6. **Input values:**
	* If you execute the workflow manually, make sure you enter a valid workflow ID. To properly link the workflow to github, you need to execute the workflow with the ID from the 'Execute Workflow Trigger'.

Once these are set, your n8n workflows will be automatically saved to your GitHub repo! 🎉
