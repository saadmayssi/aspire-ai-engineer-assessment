# AI-Powered Customer Intake & Triage Workflow

## Overview

This project implements an AI-powered intake and triage workflow for ArcVault using n8n and Gemini AI.

The workflow automates:

* Customer request ingestion
* AI-based classification
* Entity extraction and enrichment
* Routing decisions
* Escalation handling
* Structured record storage

## Technologies

* n8n
* Google Gemini 2.5 Flash
* Google Sheets
* GitHub
* Loom

## Workflow

1. Receive customer request
2. Classify request using Gemini AI
3. Extract key entities
4. Evaluate escalation criteria
5. Route ticket to appropriate queue
6. Store structured output in Google Sheets

## Routing Logic

* Bug Report → Engineering
* Feature Request → Product
* Billing Issue → Billing
* Technical Question → IT/Security
* Incident/Outage → Engineering

## Escalation Logic

Tickets are escalated when:

* Confidence score < 70%
* Incident/Outage detected
* Billing issue detected
* Multiple users affected

## Repository Contents

* workflow/ : n8n workflow export
* architecture/ : system design document
* prompts/ : AI prompts used
* outputs/ : sample outputs
* screenshots/ : workflow screenshots
