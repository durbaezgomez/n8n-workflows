# GitHub PR Review Workflow with n8n and Mistral 7B

This repository contains an **n8n workflow** designed to automate pull request reviews. By integrating GitHub triggers and the **Mistral 7B Instruct LLM** (via OpenRouter), the workflow generates concise and technical review feedback for changed files and posts it as a comment on the pull request.

<img width="1269" alt="Zrzut ekranu 2024-12-23 o 12 27 00" src="https://github.com/user-attachments/assets/98be6731-13c2-43d3-99b0-536c0c71d692" />

## Features

- **GitHub Trigger**: Executes automatically when a new pull request is created or updated.
- **File Analysis**: Fetches changed files from the pull request and their counterparts from the destination branch.
- **AI-Powered Review**: Uses Mistral 7B Instruct via OpenRouter to analyze and compare file content for:
  - Syntax improvements.
  - Logical enhancements.
  - Error detection and suggestions.
  - Concise feedback on proposed changes.
- **Automated PR Comments**: Posts the AI-generated feedback as a comment on the pull request for easy access by reviewers.

## How It Works

1. **GitHub Trigger**: Listens for pull request events.
2. **Fetch File Contents**: Retrieves the changed files and their destination branch counterparts.
3. **AI Analysis**: Sends the file content to Mistral 7B Instruct via OpenRouter for detailed feedback.
4. **PR Commenting**: Posts the AI-generated review as a comment directly on the pull request.

## Requirements

- **n8n**: Self-hosted or cloud instance.
- **OpenRouter API Key**: For accessing Mistral 7B Instruct LLM.
- **GitHub App**: With permissions for pull requests and repository contents.

## Setup

1. Clone this repository and import the provided n8n workflow.
2. Configure the following environment variables in n8n:
   - **GitHub App Credentials**: Ensure the app has access to pull requests and file contents.
   - **OpenRouter API Key**: For LLM integration.
3. Deploy the workflow and test with a sample pull request.
