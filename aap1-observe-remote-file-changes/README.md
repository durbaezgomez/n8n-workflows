# Case Directory Update Logger ⏰

## Workflow Description 📋
This n8n workflow monitors a specific folder (`/data/remote`) for newly added directories. When a new directory is detected, it extracts the case number from the directory name, records the current time in Warsaw timezone, and logs this information into a CSV file. The CSV file includes case numbers and the time they were added, making it easy to track updates. 🔔

## Used Nodes and Integrations 🔗
- **Local File Trigger**: Monitors the `/data/remote` folder for new directories. 📁
- **Set Constants**: Defines fixed paths for local images, remote data, and configuration. 📝
- **Code Node**: Extracts the case number and formats the Warsaw time. 🔧
- **Execute Command**: Appends the case number and time to a CSV file. 📄

## Setup Instructions 🔩
1. **Environment Variables**: Ensure the folder paths (`/data/remote`, `/data/local/Imagenes`, `/data/local/_n8n_db`) exist and are accessible. 📁
2. **CSV File**: The workflow creates a CSV file in the following format: `{{config_path}}/updated_cases/{{formattedDate}}_updated_cases.csv`. Make sure the `updated_cases` directory exists under your config path. 📄
3. **Timezone**: The workflow uses the `Europe/Warsaw` timezone. If you need a different timezone, update the `timezone` setting in the workflow. 🌍
4. **Permissions**: Ensure the n8n process has the necessary permissions to read from `/data/remote` and write to the CSV file. 🛠

With this setup, you’re ready to track new case directories seamlessly! 🔔⏱