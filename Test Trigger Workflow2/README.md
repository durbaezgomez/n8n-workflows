
# Execute Workflow Example

## Description
This n8n workflow demonstrates how to execute another workflow using the 'Execute Workflow' node. It's triggered manually, retrieves workflow data via a code node, and then kicks off a specified sub-workflow. 🚀

## Used Nodes and Integrations
*   **Manual Trigger:** `When clicking ‘Test workflow’`
*   **Code:** `Code` (for extracting the current workflow reference)
*   **Execute Workflow:** `Execute Workflow`, which is used to execute a sub-workflow

## Setup Instructions

1.  **Copy the Workflow:** Import this workflow into your n8n instance. ✅
2.  **Configure 'Execute Workflow' Node:**
    *   Locate the 'Execute Workflow' node. 🔧
    *   You'll need to select the specific sub-workflow you want to execute via the `workflowId` parameter. This is an id and is not the name of the workflow itself. ⚙️
    *   By default the `waitForSubWorkflow` it set to true. This means it this workflow will wait for the called subworkflow to complete. ⏱️
3.  **Run the Workflow:** Click the 'Test workflow' button to start the workflow and initiate the execution of the sub-workflow. ▶️
