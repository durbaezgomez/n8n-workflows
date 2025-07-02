# n8n Webhook Status Monitor

A dual-webhook system that provides real-time status updates for long-running n8n workflows through an auto-refreshing HTML interface.

## 🎯 Use Case

This workflow creates a user-friendly status monitoring system by:
- Serving a static HTML page that auto-polls for workflow completion
- Running background workflow logic while providing real-time feedback
- Eliminating the need for users to wait on blank screens during processing
- Providing clear success/error status updates

## ✨ Features

- **Dual Webhook Architecture**: Separate endpoints for UI and processing
- **Auto-Refreshing Status**: JavaScript polling for real-time updates
- **Visual Feedback**: Loading spinner with completion/error states
- **Self-Contained**: No external dependencies or databases required
- **Flexible Responses**: Configurable success/error/custom status codes
- **Mobile Responsive**: Works on all device types

## 🔄 How It Works

### User Flow
1. **Access URL**: User visits the service webhook URL
2. **Get HTML**: Receives auto-refreshing status page
3. **Background Processing**: Workflow logic runs in parallel
4. **Status Updates**: Page polls workflow webhook for completion
5. **Final State**: Shows success, error, or custom completion message

### Technical Flow
1. **Service Webhook** → Serves HTML with embedded JavaScript
2. **HTML JavaScript** → Polls workflow webhook every 2 seconds
3. **Workflow Webhook** → Executes business logic and returns status
4. **Status Switch** → Routes to appropriate response based on outcome

## 🌐 Webhook Endpoints

### Service Webhook (`/service_webhook`)
- **Purpose**: Entry point for users
- **Response**: HTML page with status monitor
- **Method**: GET
- **Content-Type**: `text/html`

### Workflow Webhook (`/workflow_webhook`) 
- **Purpose**: Processes business logic
- **Response**: JSON status updates
- **Method**: GET/POST
- **Content-Type**: `application/json`

## 🚀 Setup

### 1. Deploy the Workflow
1. Import the workflow into your n8n instance
2. Activate the workflow
3. Note the webhook URLs from the webhook nodes

### 2. Configure Status Logic
Modify the "Switch" node conditions based on your workflow requirements:

```javascript
// Example conditions:
// Success: when data.success === true
// Error: when error exists
// Processing: default case
```

### 3. Customize Response Messages
Update the response nodes with your desired messages:

#### Success Response
```json
{
  "status": "complete",
  "message": "Your process completed successfully!",
  "data": { /* optional result data */ }
}
```

#### Error Response
```json
{
  "status": "error", 
  "message": "Process failed. Please try again.",
  "error": "Detailed error information"
}
```

### 4. Modify HTML Interface
Customize the HTML template in "HTML Response to Webhook" node:

```html
<!-- Update styling, messages, polling interval, etc. -->
<style>
  /* Your custom CSS */
</style>

<script>
  // Adjust polling interval (default: 2000ms)
  await new Promise(resolve => setTimeout(resolve, 5000));
</script>
```

## 🎨 Customization

### Change Polling Interval
```javascript
// In the HTML JavaScript section
await new Promise(resolve => setTimeout(resolve, 3000)); // 3 seconds
```

### Add Progress Indicators
```javascript
// Track workflow steps
const steps = ['Initializing', 'Processing', 'Finalizing'];
let currentStep = 0;

// Update UI with current step
document.getElementById('status').textContent = steps[currentStep];
```

### Custom Status Messages
```javascript
// Add more status types in the switch logic
if (statusData.status === 'processing') {
  updateProgress(statusData.progress);
} else if (statusData.status === 'validation') {
  showValidationStep();
}
```

### Enhanced Error Handling
```javascript
// Add retry logic
let retryCount = 0;
const maxRetries = 3;

try {
  // ... polling logic
} catch (error) {
  if (retryCount < maxRetries) {
    retryCount++;
    setTimeout(checkWorkflowStatus, 5000);
  } else {
    showError('Maximum retries exceeded');
  }
}
```

## 🔧 Advanced Features

### Add Authentication
```javascript
// In the workflow webhook
const authToken = $('service_webhook').first().json.headers.authorization;
if (!isValidToken(authToken)) {
  return { status: 'unauthorized' };
}
```

### Progress Tracking
```javascript
// Store progress in workflow variables
$vars.progress = Math.round((currentStep / totalSteps) * 100);

// Return progress in status response
{
  "status": "processing",
  "progress": $vars.progress,
  "message": `Step ${currentStep} of ${totalSteps}`
}
```

### Multiple Status Types
```javascript
// Extend the switch node with more conditions
switch (workflowState) {
  case 'initializing': return { status: 'initializing' };
  case 'processing': return { status: 'processing', progress: 50 };
  case 'validating': return { status: 'validating' };
  case 'complete': return { status: 'complete' };
  case 'error': return { status: 'error', message: errorDetails };
}
```

## 📱 HTML Template Features

### Current Capabilities
- **Loading State**: Animated "Processing, please wait..." message
- **Success State**: Green checkmark with completion message  
- **Error State**: Red error message with retry option
- **Auto-Polling**: 2-second intervals until completion
- **Responsive Design**: Works on mobile and desktop

### Enhancement Ideas
```html
<!-- Progress bar -->
<div id="progress-container">
  <div id="progress-bar"></div>
</div>

<!-- Step indicator -->
<div id="steps">
  <span class="step active">Initialize</span>
  <span class="step">Process</span>
  <span class="step">Complete</span>
</div>

<!-- Real-time logs -->
<div id="logs">
  <div class="log-entry">Starting workflow...</div>
</div>
```

## 🛠️ Troubleshooting

### Common Issues

1. **Infinite Polling**: Check that workflow webhook returns proper status
2. **CORS Errors**: Ensure both webhooks are on same domain
3. **Timeout Issues**: Adjust polling interval for long-running processes
4. **Status Not Updating**: Verify switch node conditions are correct

### Debug Mode
Add console logging to track polling:

```javascript
console.log('Polling status:', statusData);
console.log('Current state:', document.getElementById('loading').style.display);
```

### Testing Individual Components
- Test service webhook: Visit the URL directly
- Test workflow webhook: Call it via Postman/curl
- Test switch logic: Check node execution in n8n

## 📊 Use Cases

### Perfect For
- **File Processing**: Upload and convert operations
- **Data Analysis**: Long-running calculations
- **Report Generation**: Multi-step document creation
- **API Integrations**: Third-party service calls
- **Batch Operations**: Processing multiple items

### Integration Examples
- **E-commerce**: Order processing status
- **Content Management**: Media upload and optimization  
- **Data Import**: CSV/Excel file processing
- **Notification Systems**: Bulk email/SMS sending
- **Backup Operations**: Database export/import

## 🚦 Status Response Format

### Standard Responses
```json
// Success
{ "status": "complete", "message": "Operation completed" }

// Error  
{ "status": "error", "message": "Error description" }

// Processing
{ "status": "processing", "progress": 75 }

// Custom
{ "status": "custom", "data": { "step": "validation" } }
```