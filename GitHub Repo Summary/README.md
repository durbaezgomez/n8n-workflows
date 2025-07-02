# GitHub Repository Analyzer Workflow

A specialized n8n sub-workflow that analyzes GitHub repository contents and generates comprehensive summaries using AI-powered batch processing.

## Overview

This workflow processes GitHub repository files in configurable batches, analyzes their content using Claude AI models, and produces detailed summaries including technologies used, features, and potential use cases.

## Features

- **Batch Processing**: Configurable batch sizes for efficient processing of large repositories
- **Smart File Filtering**: Filters relevant files by type and size (excludes binary files, focuses on code/docs)
- **Token Optimization**: Strips unnecessary formatting to optimize AI processing
- **Dual-Stage Analysis**: 
  - Batch-level summaries for file groups
  - Repository-level synthesis for final output
- **Structured Output**: Generates standardized JSON with technologies, features, and use cases

## Workflow Steps

1. **File Filtering**: Processes repository files and filters by type, size, and relevance
2. **Batch Creation**: Splits files into configurable batches for processing
3. **Content Optimization**: Removes formatting characters to optimize token usage
4. **Batch Analysis**: AI-powered analysis of each file batch
5. **Final Synthesis**: Combines batch summaries into comprehensive repository overview

## Configuration

- `batch_size`: Number of files per processing batch (default: 10)
- `limit`: Maximum number of files to process (default: 50)

## Output Format

```json
{
  "name": "Repository Name",
  "description": "Brief description of the repository's purpose",
  "primaryTechnologies": ["Python", "Docker", "AI/ML"],
  "features": ["Feature 1", "Feature 2", "Feature 3"],
  "useCases": ["Use case 1", "Use case 2", "Use case 3"]
}
```

## Requirements

- n8n workflow environment
- Claude AI model access (Anthropic)
- GitHub repository data input

## Usage

This sub-workflow is designed to be called from parent workflows that provide GitHub repository data. It expects repository file contents and metadata as input and returns structured analysis results.