# Local File Monitor and Log Workflow

## Description
This n8n workflow monitors a specified folder for new directories being added and logs details about them into a CSV file. It extracts case numbers from the folder names, records the time of the event in Warsaw time, and appends this information to a CSV file for tracking purposes. 🚀

## Used Nodes and Integrations
- **Local File Trigger**: Monitors a folder for new directories.
- **Code Node**: Extracts case numbers and formats the date.
- **Execute Command Node**: Logs the extracted data into a CSV file.
- **Set Node**: Defines constants for folder paths.

## Setup Instructions
1. **✅ Configure the `Local File Trigger` node**: Set the `path` parameter to the folder you want to monitor (e.g., `/data/remote`).
2. **🔧 Update the `Set Node`**: Adjust the `assignments` to match your local folder paths (`imagenes`, `remote`, `config`).
3. **🛠️ Ensure the executeCommand script works**: Update the script in the `Execute Command Node` to match your file system and ensure the paths are correct.
4. **🚨 Test the workflow**: Add a new directory to the monitored folder and verify the CSV file is updated correctly.

Enjoy seamless logging of new folders! 🎉