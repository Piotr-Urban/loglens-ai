# LogLens AI — MVP

## Problem

Analyzing large volumes of application logs manually is time-consuming.
Messages representing the same error often contain different identifiers,
timestamps, IP addresses, or request data, making them difficult to group.

## Target user

A developer or a small engineering team maintaining web applications
and investigating production incidents.

## Main workflow

1. The user uploads a log file in JSON Lines format.
2. The backend validates and parses every log entry.
3. Valid logs are stored in PostgreSQL.
4. The user browses and filters logs in the web interface.
5. Similar error messages are normalized and grouped.
6. The system detects unusual increases in error frequency.
7. Detected anomalies are converted into incidents.
8. AI generates an incident report using collected evidence.

## MVP features

- Import logs from a JSONL file
- Track the status of each import
- Validate malformed log entries
- Store structured logs in PostgreSQL
- Filter logs by time, level, and service
- Search log messages
- Generate fingerprints for similar errors
- Display error groups and their occurrence counts
- Show error frequency on a timeline
- Detect basic statistical anomalies
- Create and manage incidents
- Generate evidence-based AI incident summaries

## Outside the MVP

The first version will not include:

- Kubernetes deployment
- Mobile application
- Automatic incident remediation
- Datadog, Splunk, or AWS integrations
- Advanced user roles and permissions
- Distributed microservice architecture
- Real-time streaming from production systems

## MVP success criteria

The MVP is complete when a user can upload a prepared demo log file,
see a simulated failure detected automatically, open the resulting incident,
and read an AI-generated report referencing specific error groups and logs.