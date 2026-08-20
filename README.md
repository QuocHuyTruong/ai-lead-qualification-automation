# AI Lead Qualification Automation

An AI-powered lead qualification and routing workflow built with **n8n, Gemini API, Google Sheets, Telegram Bot API, Webhooks, and JavaScript**.

The workflow automatically receives incoming leads, analyzes them with AI, classifies them as **HOT, WARM, or COLD**, stores all lead data in Google Sheets, and sends an instant Telegram alert when a high-potential lead is detected.

## Overview

Manual lead qualification can become repetitive and slow when every inquiry must be reviewed individually.

This automation reduces that work by turning the process into:

`Incoming Lead → AI Evaluation → Classification → Storage → Alert`

The system is designed as a practical example of how AI and workflow automation can be combined to reduce repetitive sales operations.

## Business Problem

Businesses that receive customer inquiries manually often spend unnecessary time reviewing every lead, evaluating its potential, and copying information into spreadsheets.

This creates several problems:

- High-value leads may not be noticed quickly enough.
- Sales teams spend time reviewing low-quality inquiries.
- Lead data may become inconsistent or scattered.
- Repetitive manual qualification reduces productivity.

## Solution

This workflow automatically:

1. Receives lead data through a webhook.
2. Normalizes incoming information.
3. Sends the lead to Gemini for AI-based qualification.
4. Parses the AI response into structured data.
5. Classifies the lead as `HOT`, `WARM`, or `COLD`.
6. Stores all processed leads in Google Sheets.
7. Sends an immediate Telegram notification for HOT leads.

## Architecture

```text
Incoming Lead
      ↓
Webhook
      ↓
Normalize Lead
      ↓
Gemini - Qualify Lead
      ↓
Parse AI Result
      ↓
Route by Classification
   ┌──────┼──────┐
   ↓      ↓      ↓
  HOT    WARM   COLD
   │      │      │
   └──────┼──────┘
          ↓
   Google Sheets

HOT Lead
   ↓
Telegram Alert
```

## Key Features

- Webhook-based lead intake
- Automated lead normalization
- AI-powered lead qualification
- Structured AI output parsing
- HOT / WARM / COLD classification
- Automatic Google Sheets storage
- Real-time Telegram alerts for HOT leads
- Production webhook support
- Workflow execution monitoring
- API credential separation
- Demo/test lead data only

## Tech Stack

- **n8n** — workflow orchestration
- **Gemini API** — AI lead qualification
- **Google Sheets API** — lead storage
- **Telegram Bot API** — real-time notifications
- **JavaScript** — AI response parsing and data processing
- **Webhooks / REST API** — external lead intake

## Workflow

### 1. Webhook

The workflow starts when lead data is received through an HTTP POST request.

Example input:

```json
{
  "name": "Alice Nguyen",
  "email": "alice@example.com",
  "budget": 1500,
  "project": "We want to automate incoming customer inquiries and CRM updates."
}
```

### 2. Normalize Lead

Incoming data is converted into a consistent structure before further processing.

Typical fields include:

- Name
- Email
- Budget
- Project requirements

### 3. AI Qualification

Gemini analyzes the lead based on factors such as:

- Budget
- Project clarity
- Automation suitability
- Overall business potential

The AI returns structured qualification data such as:

```json
{
  "classification": "HOT",
  "score": 90,
  "reason": "The project is clear, repetitive, suitable for automation, and has a reasonable budget."
}
```

### 4. Parse AI Result

The AI output is parsed and converted into structured workflow data.

This ensures the next nodes can reliably access:

- `classification`
- `score`
- `reason`

### 5. Route by Classification

The workflow routes each lead into one of three categories:

- **HOT** — high-priority opportunity
- **WARM** — potentially valuable lead
- **COLD** — low-priority or poor-fit opportunity

### 6. Google Sheets Storage

Every processed lead is stored automatically in Google Sheets.

Stored data includes:

- Timestamp
- Name
- Email
- Budget
- Project description
- Classification
- AI score
- Qualification reason

### 7. Telegram Alert

When a lead is classified as HOT, the workflow immediately sends a Telegram notification containing the most important lead details.

Example:

```text
🔥 HOT LEAD

Name: Alice Nguyen
Email: alice@example.com
Budget: $1500

AI Score: 90/100

Project:
Automate incoming customer inquiries and CRM updates.
```

## Screenshots

### Workflow Overview

![Workflow Overview](screenshots/01-workflow-overview.png)

### Leads Dashboard

![Leads Dashboard](screenshots/02-leads-dashboard.png)

### Telegram HOT Lead Alert

![Telegram Alert](screenshots/03-hot-lead-telegram.png)

### Successful Execution

![Successful Execution](screenshots/04-successful-execution.png)

## Repository Structure

```text
ai-lead-qualification-automation/
│
├── README.md
│
├── workflow/
│   └── ai-lead-qualification.json
│
├── screenshots/
│   ├── 01-workflow-overview.png
│   ├── 02-leads-dashboard.png
│   ├── 03-hot-lead-telegram.png
│   └── 04-successful-execution.png
│
└── docs/
    └── business-case.md
```

## Security

Credentials and API keys are intentionally excluded from this repository.

The workflow uses n8n credentials for external services such as:

- Gemini API
- Google Sheets
- Telegram Bot API

Never commit real API keys, tokens, OAuth secrets, or other credentials to a public repository.

All screenshots and examples in this repository use demo/test data only.

## Potential Use Cases

The same workflow architecture can be adapted for:

- Sales teams
- Marketing agencies
- Freelancers
- Consulting businesses
- SaaS companies
- Real-estate businesses
- Service companies
- CRM lead intake systems

Possible extensions include:

- CRM integration
- Automated email follow-up
- Lead assignment
- Calendar booking
- Slack notifications
- Lead scoring dashboards
- Additional qualification rules
- Customer segmentation

## Project Goal

This project demonstrates my ability to design and build practical automation systems that combine:

- Workflow automation
- AI integration
- REST APIs
- Data processing
- External service integrations
- Business logic
- Real-time notifications

The focus is not only on connecting tools, but on turning a repetitive business process into an automated workflow.
