# TableCoach

**Proprietary restaurant operations analytics and decision-support platform**  
*Public technical showcase — production source and operational data remain private.*

TableCoach is an operations-focused application designed to turn recurring restaurant performance data into information managers can review, validate, and act on.

The project grew from firsthand restaurant operations experience and is informed by practical management workflows. Any evaluation involving a restaurant location is informal and should not be interpreted as corporate approval or endorsement. This repository documents the product and engineering work without publishing internal operational data or the proprietary production codebase.

## What TableCoach Does

TableCoach centers on a practical management workflow:

**scorecard import → data-quality review → approval → performance analysis → coaching actions → manager reporting → outcome validation**

The application is designed to help managers move from a recurring scorecard or report to specific follow-up work rather than treating analytics as a passive dashboard.

### Core capabilities

- Import recurring scorecards from PDF and CSV sources
- Parse and normalize operational performance data
- Surface low-confidence values and anomalies for human review
- Reconcile employee identities across imports
- Track individual and team performance over time
- Visualize historical trends and coaching themes
- Convert performance gaps into assigned follow-up tasks
- Produce manager-ready weekly reports and printable materials
- Maintain audit-oriented workflows around imports and corrections
- Separate modeled improvement opportunities from confirmed business outcomes

## Why I Built It

Restaurant reporting often arrives as a snapshot: useful numbers, but limited support for preserving context, comparing performance over time, validating questionable imports, or turning findings into a repeatable coaching process.

TableCoach explores what happens when those pieces are treated as one workflow instead of separate spreadsheets, reports, notes, and conversations.

The project also gives me a useful engineering constraint: the software has to make sense to people working in a fast operational environment. A technically interesting system is not useful if the manager cannot quickly understand what changed, why it matters, and what action should follow.

## Technical Focus

The private implementation currently uses technologies including:

- **Python / Flask** for application and service logic
- **JavaScript / Chart.js** for interactive analytics
- **PDF and CSV ingestion** for recurring operational data
- **Structured validation** around imported and generated values
- **Local JSON storage** for development/testing workflows
- **PostgreSQL-oriented production architecture** for multi-user persistence, transactions, backups, and auditability

The engineering work extends beyond charting. Particular attention is given to **data provenance, validation, reviewability, identity reconciliation, workflow state, and the distinction between estimates and confirmed outcomes**.

## Data Quality & Trust

Operational analytics becomes dangerous when a polished interface makes questionable data look authoritative.

TableCoach therefore treats import review as part of the product rather than an implementation detail. The system is designed to expose suspicious or low-confidence values, support corrections before approval, retain the context around imports, and avoid silently converting uncertain data into management recommendations.

Similarly, modeled impact and confirmed results are kept conceptually separate. A recommendation can estimate where an opportunity may exist; later operational/POS results are what establish whether the expected improvement actually occurred.

## Product Status

TableCoach is an **active proprietary project in development**. The public repository does not contain production code or data and cannot independently demonstrate the full feature list.

Current work includes the end-to-end scorecard/coaching workflow, import validation, trend analysis, manager reporting, and production-oriented persistence and audit concerns.

Future public updates may include sanitized screenshots, synthetic-data demonstrations, and architecture diagrams as the interface and product direction stabilize.

## Privacy & Proprietary Source

This repository is intentionally a showcase rather than the production repository.

The private codebase may contain or interact with internal operational information and is being developed with potential future commercial use in mind. For that reason:

- production source code is not published here;
- real employee or internal operational data is not published here;
- screenshots or demonstrations added in the future will use sanitized or synthetic information;
- this project should not be interpreted as an official LongHorn Steakhouse or Darden Restaurants product.

## My Role

I designed and developed TableCoach based on a combination of software engineering and firsthand restaurant operations experience. My work includes the application architecture, ingestion and validation workflow, analytics, decision-support concepts, reporting, and the mechanisms used to distinguish modeled recommendations from validated results.

## Showcase Documentation

- [Architecture Overview](docs/ARCHITECTURE.md)
- [Data & Decision Workflow](docs/DATA_WORKFLOW.md)

---

**Status:** Proprietary project in active development  
**Source:** Private  
**Public repository:** Product and engineering showcase only
