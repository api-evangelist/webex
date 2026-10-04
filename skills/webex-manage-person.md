---
name: webex-manage-person
description: Create, retrieve, update, and delete a person in the Webex People API.
api: openapi/webex-cloud-calling-openapi.yml
operations:
- CreateAPerson
- GetPersonDetails
- UpdateAPerson
- DeleteAPerson
generated: '2026-10-04'
method: generated
generator: extract-docs-artifacts.py skills (local)
source: openapi/webex-cloud-calling-openapi.yml ; every operationId checked against the contract
---

# webex-manage-person

Create, retrieve, update, and delete a person in the Webex People API.

## Steps

1. 1. Use `CreateAPerson` with required body fields for the new person.
2. 2. Use `GetPersonDetails` with the `personId` path parameter to verify creation.
3. 3. Use `UpdateAPerson` with the `personId` path parameter and the fields to modify.
4. 4. Use `DeleteAPerson` with the `personId` path parameter to remove the person.

## Rules

- Include a Bearer token in the `Authorization` header (e.g., `Authorization: Bearer <token>`).
- When listing people, support pagination using the `page` and `limit` query parameters.
