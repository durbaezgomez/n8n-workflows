# n8n Grafana Loki Logger

Automatically capture and forward n8n workflow execution data to Grafana Loki for centralized logging and monitoring.

## 🎯 Use Case

This workflow provides automated logging capabilities for your n8n workflows by:
- Capturing execution data from completed workflows
- Filtering relevant user interactions
- Formatting data for Grafana Loki ingestion
- Providing centralized logging for monitoring and debugging

## ✨ Features

- **Execution Monitoring**: Captures detailed execution data from any n8n workflow
- **Smart Filtering**: Only logs genuine user interactions (excludes system/test messages)
- **Loki Integration**: Sends structured logs directly to Grafana Loki
- **Real-time Logging**: Processes executions as they complete
- **Structured Data**: Formats execution data for easy querying in Grafana

## 🔄 How It Works

1. **Trigger**: Called by other workflows with an execution ID
2. **Wait**: 5-second delay to ensure execution data is available
3. **Fetch**: Retrieves execution details from n8n API
4. **Filter**: Excludes test messages (those containing "###")
5. **Format**: Structures data for logging
6. **Send**: Pushes formatted logs to Grafana Loki

## 📊 Data Structure

The workflow captures:
- **Execution metadata**: ID, status, timing
- **Node data**: All node executions and their results
- **Chat interactions**: User inputs and responses
- **Workflow context**: Names, types, and execution flow

## 🚀 Setup

### 1. Grafana Loki Configuration

1. Set up a Grafana Cloud account or self-hosted Loki instance
2. Generate an API key with write permissions
3. Note your Loki endpoint URL

### 2. n8n API Credentials

1. Create n8n API credentials in your instance
2. Ensure the API user has execution read permissions

### 3. Workflow Configuration

Update the following in the workflow:

#### Loki Endpoint
```javascript
// In "Loki - Push logs" node
url: "https://logs-prod-025.grafana.net/loki/api/v1/push"
```

#### Authorization Header
```javascript
// Replace with your Loki API key
"Authorization": "Bearer YOUR_USER_ID:YOUR_API_KEY"
```

#### Stream Labels
```javascript
// In "Format Loki stream object" node
stream: { logs: "your-environment-name" }
```

### 4. Integration with Other Workflows

To enable logging in your workflows, add an "Execute Workflow" node at the end:

```json
{
  "workflowId": "LOGGER_WORKFLOW_ID",
  "executionData": {
    "executionId": "={{ $execution.id }}"
  }
}
```

## 🔧 Customization

### Change Filter Criteria
Modify the filter conditions to capture different types of executions:

```javascript
// Current: Excludes messages with "###"
// Alternative: Include only specific workflow types
$json.data.resultData.runData.Webhook[0].data.main[0][0].json.body.workflowType === "chat"
```

### Add More Context
Enhance the log formatting to include additional metadata:

```javascript
return {
  log: {
    executionId: itemData.id,
    workflowId: itemData.workflowId,
    timestamp: itemData.startedAt,
    duration: itemData.stoppedAt - itemData.startedAt,
    // ... existing data
  }
}
```

### Different Log Streams
Use different Loki streams for different workflow types:

```javascript
const stream = chatInfo.type === 'support' ? 
  { logs: "support-chats" } : 
  { logs: "general-executions" }
```

## 📈 Grafana Queries

Example LogQL queries for monitoring:

### Recent Executions
```logql
{logs="your-environment-name"} | json
```

### Error Detection
```logql
{logs="your-environment-name"} | json | status != "success"
```

### Chat Volume
```logql
rate({logs="your-environment-name"} | json | chatInput != ""[5m])
```

### Execution Duration
```logql
{logs="your-environment-name"} | json | duration > 10000
```

## 🛠️ Troubleshooting

### Common Issues

1. **Missing Execution Data**: Increase wait time if executions aren't fully processed
2. **Loki Authentication**: Verify API key format and permissions
3. **Filter Too Restrictive**: Check if filter conditions are excluding valid executions
4. **Rate Limits**: Monitor Loki ingestion limits and adjust accordingly

### Debug Mode

Enable debug logging by adding console.log statements:

```javascript
// In format log node
console.log("Execution data:", itemData);
console.log("Filtered data:", chatInfo);
```

## 📊 Monitoring Benefits

- **Performance Tracking**: Monitor workflow execution times
- **Error Detection**: Quickly identify failed executions
- **Usage Analytics**: Track user interaction patterns
- **System Health**: Monitor overall n8n instance performance
- **Debugging**: Detailed execution logs for troubleshooting

## 🔒 Security Notes

- API keys are embedded in the workflow - ensure proper access controls
- Consider using environment variables for sensitive credentials
- Regularly rotate API keys and monitor access logs
- Filter sensitive data before logging to Loki

## 📝 Requirements

- n8n instance with API access
- Grafana Cloud account or self-hosted Loki
- Appropriate API permissions for both services