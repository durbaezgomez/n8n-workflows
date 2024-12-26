
# Save Workflow To GitHub Subworkflow

🚀 **Description:**

This workflow acts as a subworkflow designed to be triggered by another main workflow. It receives workflow data and, based on the `workflowId`, executes another n8n workflow. The primary goal is to allow modular execution of workflows, enabling a 'save to GitHub' functionality where one workflow can trigger and execute another, for example, the workflow which saves a workflow definition file to git.

⚙️ **Used Nodes and Integrations:**

*   **Manual Trigger:**  Initiates the subworkflow when manually executed within a main workflow.
*   **Code:**  A node to access the workflow data for use in the workflow 
*   **Execute Workflow:** Triggers another n8n workflow based the extracted workflow ID given by the caller.


🛠️ **Setup Instructions:**

1.  **No Credentials Required:** No external service credentials are needed for this workflow.
2.  **Subworkflow Activation**: This workflow is meant to be triggered by another workflow using the `Execute Workflow` node. Therefore, no external triggering is required.
3.  **`workflowId` Value:** When triggering this workflow in the `Execute Workflow` node of another workflow, make sure the `workflowId` parameter points to the workflow you'd like to execute.. 
4.  **Input:** No specific input data is required for the execution of the subworkflow. Note, however, that the workflow to execute is given by its `workflowId` using a parameter. This ID parameter should be extracted from the main workflow in advanced.

✅ Once setup, this subworkflow can be incorporated into your main workflows to execute further workflows.
