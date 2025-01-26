# n8n Workflow to Generate README for GitHub

## Description 🚀
This workflow automatically generates a README file for your n8n workflows and pushes it to a specified GitHub repository. It extracts information from the workflow itself, such as the title, nodes used, and any setup instructions, to create a clear and concise README.md file. This saves you time and effort while ensuring your workflows are well-documented.

## Used Nodes and Integrations 🔌
* **n8n Nodes:**
    * Execute Workflow Trigger
    * Code
    * Set
    * Manual Trigger
    * n8n
    * Sticky Note
* **Langchain Nodes:**
    * Agent
    * Openrouter (google/gemini-pro-1.5)
* **Integrations:**
    * GitHub
    * OpenRouter.ai

## Setup Instructions 🔧
1. **Workflow ID:** Set the `Workflow ID` in the *Get Workflow by ID* node. You can trigger the workflow manually or by using the webhook URL of the `Execute Workflow Trigger` node, passing in the workflow ID you wish to generate a README for. 
2. **GitHub Credentials:** Configure your GitHub credentials in the respective nodes (*Create JSON file*, *Create README*, *Edit JSON file* and *Update README*).
3. **Repository:** Set the `Repository` name in the *Check if workflow is on GitHub* node under the parameter tab. This should point to the GitHub repository where you want to store the README files.
4. **JSON Filename**: This workflow generates a JSON file containing your n8n workflow definition. The title of this JSON file will be formatted as *your-workflow-name*.json file. This process is handled within the workflow itself using a *Set* node to format the name and convert it accordingly.
5. **OpenRouter Credentials:** Configure your OpenRouter credentials in the *Openrouter* node.
6. **Test and Deploy:**  Click "Test workflow" to ensure everything is working correctly. Once you're happy, deploy the workflow.✅

This workflow assumes your repos are hosted as https://github.com/<username>/AAP_1-12-24_automations.  Change this within the *Check if workflow is on GitHub* node parameters tab if this is different for your setup.  This should be adjusted to point to your main repository for storing the workflows and their respective README files.