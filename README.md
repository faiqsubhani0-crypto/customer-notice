# Customer Notice / SupportDesk Compliance Regression

This repository contains a small SupportDesk-style Python package used to model a compliance regression scenario across customer support operations. The codebase includes modules for authentication, ticket normalization, workflow transitions, ticket search, SLA deadline handling, CSV imports, export path safety, rate limiting, and customer notification formatting.

The project is designed around a realistic support desk release scenario where multiple independent subsystems must be updated to follow active operational policies while ignoring deprecated legacy behavior.

## Project Purpose

The purpose of this repository is to provide a compact codebase for evaluating and testing regression fixes across several support-desk subsystems. The task requires understanding active policy requirements, identifying outdated implementation behavior, and updating the source files so that all public functions follow the current release rules.

## Main Functional Areas

The repository includes the following modules:

| Module | Purpose |
|---|---|
| `auth.py` | Parses and validates Bearer authorization headers |
| `tickets.py` | Normalizes ticket fields such as subject, priority, tags, and customer ID |
| `workflow.py` | Handles ticket status transitions |
| `search.py` | Searches visible tickets while respecting archived/internal visibility rules |
| `sla.py` | Calculates SLA due dates using priority and timezone rules |
| `importers.py` | Imports tickets from CSV data |
| `exports.py` | Safely resolves export paths inside an allowed base directory |
| `rate_limits.py` | Applies sliding-window request rate limiting |
| `notifications.py` | Builds customer-facing ticket status notices |

## Active Policy Documents

The expected behavior is described by the active policy and release documents used with this repository:

- `API_CONTRACT.md`
- `INCIDENT_REPORTS.md`
- `SECURITY_REVIEW.md`
- `RELEASE_MATRIX.md`

A deprecated legacy notes file may also exist in the related benchmark task. That file represents outdated behavior and should not be used as the source of truth.

## Expected Public Functions

The release matrix preserves these public functions:

```python
supportdesk.auth.parse_bearer_token
supportdesk.tickets.normalize_ticket
supportdesk.workflow.next_status
supportdesk.search.search_tickets
supportdesk.sla.due_at
supportdesk.importers.import_tickets_csv
supportdesk.exports.safe_export_path
supportdesk.rate_limits.allow_request
supportdesk.notifications.build_notice
