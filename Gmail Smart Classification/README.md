# AI Email → Slack Notifier (n8n)

An n8n workflow that monitors your Gmail inbox, filters out noise, and uses AI to forward only important or urgent emails to Slack.

## Overview

This workflow reduces inbox overload by combining rule-based filtering with AI-powered email classification. Incoming emails are analyzed, scored, and only high-signal messages trigger Slack notifications.

## Features

- Real-time Gmail monitoring  
- Spam and newsletter pre-filtering  
- AI-based email classification and summarization  
- Priority scoring and importance thresholds  
- Rate limiting to prevent notification spam  
- Rich Slack notifications with summaries and action items  
- Automatic Gmail labeling for processed emails  

## How It Works

1. New emails are received via Gmail Trigger  
2. Obvious spam and promotions are filtered out  
3. AI classifies emails by urgency, priority, and required action  
4. Guardrails decide whether a Slack notification should be sent  
5. Important emails are sent to Slack and labeled in Gmail  

## Setup

1. Import the workflow into n8n  
2. Configure Gmail, Slack, and AI provider credentials  
3. Adjust filters, thresholds, and rate limits if needed  
4. Activate the workflow  

## Use Cases

- Founders and solo operators  
- Teams that rely on Slack for communication  
- Anyone looking to reduce inbox noise  