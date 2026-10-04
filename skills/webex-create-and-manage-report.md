---
name: webex-create-and-manage-report
description: Create a new partner report, retrieve its details, and list existing reports.
api: openapi/webex-cloud-calling-openapi.yml
operations:
- createAReport
- getReportDetails
- listReports
generated: '2026-10-04'
method: generated
generator: extract-docs-artifacts.py skills (local)
source: openapi/webex-cloud-calling-openapi.yml ; every operationId checked against the contract
---

# webex-create-and-manage-report

Create a new partner report, retrieve its details, and list existing reports.

## Steps

1. 1. Call `createAReport` with required body fields as defined in the contract.
2. 2. Call `getReportDetails` with the `reportId` returned from step 1, using the path parameter `reportId`.
3. 3. Call `listReports` with optional query parameters `page` and `limit` for pagination.

## Rules

- Auth: Include a Bearer token in the `Authorization` header (e.g., `Authorization: Bearer <token>`).
- Pagination: Use `page` and `limit` query parameters on `listReports` to page through results.
- Idempotency: Not required for these operations.
- Errors: On rate‑limit exhaustion the API returns no specific HTTP status code.
