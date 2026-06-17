# Gemini Prompt Documentation

## Purpose

Google Gemini was used to classify customer support requests, extract important information, generate a confidence score, and produce a structured JSON response for downstream routing and storage.

## Main Prompt

You are a support ticket triage AI.

Analyze the customer message and return ONLY valid JSON.

Classify the ticket into one of the following categories:

* Bug Report
* Feature Request
* Billing Issue
* Technical Question
* Incident/Outage

Determine the priority:

* Low
* Medium
* High

Return the following fields:

{
"category": "",
"priority": "",
"confidence": 0,
"core_issue": "",
"identifiers": [],
"urgency_signal": "",
"summary": ""
}

Rules:

* Return only valid JSON.
* Do not include markdown.
* Do not wrap the output in code blocks.
* Do not include explanations.
* Confidence must be between 0 and 100.
* Extract account IDs, invoice numbers, URLs, usernames, and other identifiers when available.

## Example Output

{
"category": "Bug Report",
"priority": "High",
"confidence": 98,
"core_issue": "Authentication failure preventing account access.",
"identifiers": ["arcvault.io/user/jsmith"],
"urgency_signal": "Persistent login failure",
"summary": "User is unable to access their account due to a 403 Forbidden error."
}

## Design Decisions

### Why Gemini?

Gemini provides strong text classification, entity extraction, summarization, and structured JSON generation capabilities with minimal prompt engineering.

### Why JSON Output?

Structured JSON allows downstream automation components to reliably consume AI-generated data and route tickets without additional parsing logic.

### Why Confidence Scoring?

Confidence scores support human-in-the-loop workflows by identifying uncertain classifications and triggering escalation when necessary.

### Why Restricted Categories?

Limiting categories ensures consistent routing decisions and simplifies queue management.
