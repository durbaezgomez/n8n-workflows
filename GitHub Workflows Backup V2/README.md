# n8n Workflow GitHub Backup

Automatically backup all your n8n instance workflows to a GitHub repository with intelligent change detection and organized file structure.

## 🎯 Use Case

This workflow provides automated backup and version control for your n8n workflows by:
- Syncing all workflows from your n8n instance to GitHub
- Detecting changes and only updating modified workflows
- Organizing backups in a date-based folder structure
- Providing notifications on completion and failures

## ✨ Features

- **Automatic Scheduling**: Runs daily at 1:33 AM to backup all workflows
- **Smart Change Detection**: Compares workflows with existing GitHub files to avoid unnecessary commits
- **Organized Structure**: Files saved as `YYYY/MM/workflow-id.json`
- **Memory Efficient**: Uses subworkflow execution to handle large numbers of workflows
- **Error Handling**: Continues processing even if individual workflows fail
- **Slack Notifications**: Optional completion and error notifications
- **Manual Trigger**: Can be executed manually for immediate backup

## 📁 File Structure

```
your-repo/
├── backup-path/
│   ├── 2024/
│   │   ├── 01/
│   │   │   ├── workflow-id-1.json
│   │   │   └── workflow-id-2.json
│   │   └── 02/
│   │       ├── workflow-id-3.json
│   │       └── workflow-id-4.json
│   └── 2025/
│       └── 01/
│           └── workflow-id-5.json
```

## 🚀 Setup

### 1. GitHub Repository Setup

1. Create a GitHub repository for your workflow backups
2. Generate a GitHub Personal Access Token with `repo` permissions
3. Add the token to your n8n credentials as a GitHub credential

### 2. n8n Variables Configuration

Set up the following variables in your n8n instance:

| Variable | Description | Example |
|----------|-------------|---------|
| `repo_owner` | GitHub username or organization | `your-username` |
| `repo_name` | Repository name | `n8n-workflows-backup` |
| `repo_path` | Path within repo (with trailing slash) | `workflows/` |

### 3. Slack Integration (Optional)

If you want notifications:
1. Create a Slack app and get a bot token
2. Add the Slack credential to n8n
3. Update the channel name in the notification nodes (default: `#notifications`)

### 4. Workflow Import

1. Import this workflow into your n8n instance
2. Configure the GitHub credential in all GitHub nodes
3. Configure Slack credentials if using notifications
4. Test with manual execution

## ⚙️ How It Works

### Main Workflow
1. **Trigger**: Scheduled daily or manual execution
2. **Fetch Workflows**: Gets all workflows from n8n API
3. **Process**: Loops through each workflow and calls the subworkflow
4. **Notify**: Sends completion notification

### Subworkflow
1. **Get Existing**: Attempts to fetch existing file from GitHub
2. **Compare**: Compares current workflow with GitHub version
3. **Update**: Creates new file or updates existing file if different
4. **Skip**: Does nothing if workflow hasn't changed

## 🔧 Customization

### Change Schedule
Modify the Schedule Trigger node to run at different times:
```json
{
  "triggerAtHour": 2,
  "triggerAtMinute": 0
}
```

### Disable Notifications
Remove or disable the Slack notification nodes if not needed.

### Different Repository Structure
Modify the `Create sub path` node to change the folder structure:
```javascript
// Current: YYYY/MM/
// Alternative: workflows/YYYY-MM-DD/
$('Execute Workflow Trigger').first().json.createdAt
```

## 📊 Performance

- **Tested with**: 1,423 workflows on n8n v1.44.1
- **Initial run**: ~30 minutes
- **Subsequent runs**: ~12 minutes (only changed workflows)
- **Memory usage**: Optimized through subworkflow execution

## 🛠️ Troubleshooting

### Common Issues

1. **GitHub API Rate Limits**: The workflow handles this by processing workflows individually
2. **Large Workflows**: Files too large for GitHub API are handled with direct download
3. **Missing Variables**: Ensure all required variables are set in n8n settings

### Error Handling

- Failed individual workflows don't stop the entire process
- Error notifications sent to Slack for failed workflows
- Workflow continues processing remaining items

## 📝 Notes

- The workflow calls itself recursively to optimize memory usage
- JSON files are formatted with proper indentation for readability
- Workflow IDs are used as filenames for easy identification
- Creation date determines folder structure (YYYY/MM format)