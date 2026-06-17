# AI-Powered Customer Intake & Triage Workflow

## Architecture Report

### Candidate

Saadeddine El Mayssi

---

# 1. Executive Summary

This project implements an AI-powered customer intake and triage workflow for ArcVault using n8n, Google Gemini, and Google Sheets.

The objective is to automate the initial processing of customer support requests by classifying tickets, extracting key information, determining escalation requirements, routing requests to the appropriate business queue, and storing structured results for operational visibility.

The solution reduces manual effort, improves routing consistency, and enables scalable handling of customer requests while maintaining human oversight through escalation mechanisms.

---

# 2. Solution Architecture

The workflow is built using n8n as the orchestration platform and Google Gemini as the AI engine.

The processing pipeline consists of six stages:

1. Ticket Ingestion
2. AI Classification & Enrichment
3. JSON Transformation
4. Escalation Evaluation
5. Queue Routing
6. Data Persistence

### High-Level Workflow

Customer Ticket
→ Gemini AI Analysis
→ Structured JSON Output
→ Escalation Logic
→ Queue Assignment
→ Google Sheets Storage

---

# 3. AI Classification & Enrichment

Google Gemini is responsible for understanding the customer request and converting unstructured text into structured data.

The model classifies tickets into one of the following categories:

* Bug Report
* Feature Request
* Billing Issue
* Technical Question
* Incident/Outage

In addition to classification, Gemini extracts operationally useful information including:

* Priority Level
* Confidence Score
* Core Issue
* Relevant Identifiers
* Urgency Signals
* Human-readable Summary

Example extracted identifiers include:

* Usernames
* Account IDs
* URLs
* Invoice Numbers
* System References

The AI response is returned as structured JSON to support downstream automation.

---

# 4. Escalation Logic

Human oversight remains an important component of support operations.

The workflow routes tickets to an Escalation Queue when predefined conditions indicate uncertainty or elevated business impact.

Current escalation conditions include:

* Confidence score below 70%
* Incident or outage detection
* Billing-related issues
* High-impact indicators such as multiple users affected

This approach ensures that potentially critical requests receive human review before final processing.

In a production environment, escalation rules could be expanded to include:

* Customer sentiment analysis
* SLA impact assessment
* Revenue exposure calculations
* Dynamic billing discrepancy thresholds
* Historical incident correlation

---

# 5. Queue Routing Strategy

Tickets that do not require escalation are automatically routed to the appropriate business team.

| Category           | Destination Queue |
| ------------------ | ----------------- |
| Bug Report         | Engineering       |
| Feature Request    | Product           |
| Billing Issue      | Billing           |
| Technical Question | IT/Security       |
| Incident/Outage    | Engineering       |

This routing strategy reduces manual triage effort and ensures requests reach the correct stakeholders quickly.

---

# 6. Data Storage

After processing, all ticket information is stored in Google Sheets.

The following fields are recorded:

* Source
* Category
* Priority
* Confidence Score
* Core Issue
* Identifiers
* Urgency Signal
* Queue
* Escalation Status
* Summary

The stored dataset provides a lightweight operational dashboard and creates an auditable history of routing decisions.

---

# 7. Technology Stack

### Orchestration

* n8n

### Artificial Intelligence

* Google Gemini 2.5 Flash

### Data Storage

* Google Sheets

### Version Control

* GitHub

### Demonstration

* Loom

---

# 8. Future Enhancements

Several improvements could further increase the value of the solution:

### CRM Integration

Automatic creation of tickets in platforms such as Zendesk, Jira, or ServiceNow.

### Advanced Escalation

Dynamic risk scoring based on customer impact, revenue exposure, and SLA requirements.

### Sentiment Analysis

Identification of frustrated or high-risk customers for priority handling.

### Feedback Loop

Human reviewer decisions could be captured and used to improve future AI classifications.

### Analytics Dashboard

Real-time reporting on ticket volume, categories, routing performance, and escalation trends.

---

# 9. Conclusion

The proposed solution demonstrates how AI can automate customer intake and triage processes while preserving human oversight for high-risk scenarios.

By combining n8n workflow automation with Google Gemini's natural language understanding capabilities, the system can classify requests, extract business-relevant information, route tickets intelligently, and maintain structured operational records.

The design is scalable, easy to maintain, and provides a strong foundation for future integration with enterprise support platforms.
