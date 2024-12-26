
# Save Workflow To GitHub

## Description

This workflow automatically generates a README.md file for your n8n workflows and adds them to GitHub, along with the workflow's JSON data. It leverages an AI agent to summarize the workflow, extract key information, and present it in a user-friendly format. 🚀

## Used Nodes and Integrations

*   **Trigger Nodes:**
    *   Execute Workflow Trigger
    *   Manual Trigger
*   **Core Nodes:**
    *   Code
    *   Set
    *   n8n
    *   Sticky Note
*   **Integrations:**
    *   GitHub
    *   Langchain (AI Agent and OpenRouter)

## Setup Instructions

To use this workflow successfully, follow these steps:

1.  **n8n API Credentials:** ✅
    *   Make sure you have configured the **n8n API** credential for the `Get Workflow by ID` and `Get Workflow From List` nodes. This allows the workflow to fetch its own data.
    
2.  **GitHub OAuth2 Credentials:** ✅
    *   Ensure the **GitHub OAuth2 API** credential is set up correctly to allow writing to your repository in the `Update readme`, `Create JSON file`, `Create README`, and `Edit JSON file` nodes.

3.  **Openrouter Credentials:** ✅
    *   Confirm that your **OpenRouter API** Key is configured under the `Openrouter` node's credentials settings. This is used by the AI Agent. 

4.  **Workflow ID:** 🔧
    *   Update the `Get Workflow From List` in the `When clicking 'Test workflow'` branch node to **set your n8n workflow id**, the one you are going to save on Github.
5.  **GitHub Repository:** 🔧
    *   In all Github nodes (`Update readme`, `Create JSON file`, `Create README`, `Edit JSON file` and `Check if workflow is on GitHub`), set the  `repository` property to your **target Github repository**.

6. **Run the `When clicking 'Test workflow'` branch or trigger by using the `Execute Workflow Trigger` by passing the ID of the workflow you want to save on Github**

That's pretty much it! Enjoy automatically documenting your n8n workflows on GitHub! 🎉
