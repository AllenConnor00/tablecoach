# TableCoach Architecture Overview

This document describes the public, non-proprietary architecture of TableCoach. It intentionally omits production source code, internal operational data, credentials, and implementation details that would expose the private application.

## System Shape

At a high level, TableCoach is organized around five responsibilities:

```text
Operational reports
       │
       ▼
PDF / CSV ingestion
       │
       ▼
Parsing + normalization
       │
       ▼
Human data-quality review
       │
       ▼
Approved operational dataset
       │
       ├────────► Trend / performance analysis
       │
       ├────────► Coaching workflow
       │
       └────────► Manager reporting
                         │
                         ▼
                  Outcome validation
```

The important architectural boundary is between **imported information** and **approved information**. Parsing a value does not automatically make it trusted enough to drive management decisions.

## Application Layer

The private application uses a Python/Flask backend with browser-based management and analytics surfaces. Backend services separate responsibilities such as ingestion, validation, employee reconciliation, analytics, reporting, and persistence rather than treating the entire workflow as one monolithic import script.

The frontend uses ordinary web technologies and Chart.js for interactive performance views. The interface is designed around manager workflows rather than around exposing every available metric at once.

## Ingestion

TableCoach accepts recurring operational data from PDF and CSV sources.

An ingestion pipeline can:

1. identify and parse expected fields;
2. normalize values into application data structures;
3. associate records with known employees and reporting periods;
4. attach confidence or review context where appropriate;
5. route questionable values through a human review step;
6. approve the resulting import before it becomes part of the trusted analytical history.

This makes ingestion a controlled workflow rather than a blind file conversion.

## Identity Reconciliation

Employee names and identifiers can vary across recurring reports. TableCoach maintains persistent employee identity separately from any single imported spelling or row representation.

The goal is to avoid fragmenting one person's history because an upstream report changes formatting, while also avoiding aggressive automatic matching that could silently merge two different employees.

## Analytics

Approved historical data supports individual and team analysis over time. The application can use that history to surface trends, performance gaps, and areas that may warrant coaching attention.

The analytics layer is intentionally downstream of validation. A sophisticated chart based on a bad import is still a bad result.

## Coaching Workflow

TableCoach treats coaching as workflow state rather than as an annotation attached to a chart.

A performance finding can become a follow-up action with context that survives beyond the current reporting period. This allows managers to connect recurring measurements with actual coaching work and later results.

## Reporting

Manager-oriented reports summarize the information needed for recurring operational review without requiring the user to reconstruct the story from multiple screens.

Printable materials are supported because physical handoffs and conversations remain part of many restaurant management workflows.

## Persistence

Development and local testing can use JSON-backed storage for simplicity and portability.

The production-oriented design supports PostgreSQL-backed persistence for concerns including:

- multi-user transaction safety;
- durable application state;
- automated backups;
- audit logging;
- concurrent manager workflows.

## Security & Privacy

TableCoach is built around operational information that may be sensitive even when it is not traditionally considered security data.

Public showcase material therefore contains no real employee records, internal scorecards, credentials, or proprietary operational datasets. Future demonstrations will use synthetic or deliberately sanitized data.

## Design Principle

The core architectural principle is simple:

> **Do not turn uncertain data into confident decisions.**

Import confidence, human review, provenance, correction, and outcome validation are part of the application architecture because trustworthiness is a product feature, not merely a parsing concern.
