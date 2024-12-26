
# Execute Workflow Example

## Description
This workflow is designed to execute another n8n workflow using its ID. It starts with a manual trigger, fetches the current workflow data, and then uses the Execute Workflow node to run a sub-workflow. 🚀

## Used Nodes and Integrations
*   **When clicking ‘Test workflow’**:  Manual trigger to initialize the workflow.
*   **Code**: Node to extract the workflow details using JavaScript.
*   **Execute Workflow**: Node to execute a specified sub-workflow.

## Setup Instructions

1.  **Copy workflow** into your n8n instance. ✅
2.  **Execute Workflow Node Configuration**: In the `Execute Workflow` node, locate the `Workflow ID` field.
3.  **Set the workflow for execution**. The field `hkydiXI5SkOOnPtc` needs to be replaced with your sub-workflow ID. 🔧
4.  **Test:** Hit `Execute Workflow` on the `Manual Trigger` node to run the whole process. ✅

That's it! You're all set to start executing workflows.
