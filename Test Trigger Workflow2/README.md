# Execute Workflow Sub

## Description
This workflow is designed to execute another n8n workflow. It's triggered manually and passes the current workflow details to the execution workflow node. 🚀 This is useful for creating modular workflows and running sub workflows.

## Used Nodes and Integrations
*   **Manual Trigger:**  This node initiates the workflow when you click 'Test workflow'.
*   **Code:** Extracts the current workflow object as a payload
*   **Execute Workflow:** Executes the n8n workflow specified by ID.

## Setup Instructions
Before using this workflow, you'll need to do the following: 🔧

1.  **Configure Execute Workflow Node:**
    *   ✅ Locate the 'Execute Workflow' node.
    *   ✅ Set the `Workflow ID` field to the ID of the n8n workflow you intend to execute. You can search this by the save workflow name, but it must be a saved workflow.

2.  **No Environment Variables or Credentials:** This workflow does not rely on any specific environment variables or credential configurations.
