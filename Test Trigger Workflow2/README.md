
# Execute Workflow Subworkflow

## Description

This workflow is designed to execute a specified sub-workflow. It starts with a manual trigger, retrieves the current workflow's information, and then executes the sub-workflow defined by its ID. 🚀

## Used Nodes and Integrations

*   **Manual Trigger:**  Triggers the workflow manually - perfect for testing! 
*   **Code:**  Executes custom JavaScript code to access workflow information. 💻
*   **Execute Workflow:** Runs another n8n workflow as a sub-workflow. ⚙️

## Setup Instructions

To get this workflow up and running, follow these steps:

1.  **Import the Workflow:** Copy the provided JSON and import it into your n8n instance. 📦
2.  **Configure the Execute Workflow Node:** 🔧
    *   Locate the 'Execute Workflow' node in the workflow canvas.
    *   In the 'workflowId' parameter,  choose a workflow from the list, or enter the ID of the workflow you want to execute. ✅


That's all folks! You should now be able to execute sub-workflows with this setup. 😉
