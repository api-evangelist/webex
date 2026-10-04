---
name: webex-list-and-get-user
description: Retrieve a list of users and then fetch details for a specific user.
api: openapi/webex-users-api-openapi.yml
operations:
- getAllConfigUser
- getConfigUser
generated: '2026-10-04'
method: generated
generator: extract-docs-artifacts.py skills (local)
source: openapi/webex-users-api-openapi.yml ; every operationId checked against the contract
---

# webex-list-and-get-user

Retrieve a list of users and then fetch details for a specific user.

## Steps

1. 1. Call `getAllConfigUser` with query parameters `page` and `limit` to paginate through the user list.
2. 2. From the response, obtain the desired user `id`.
3. 3. Call `getConfigUser` with path parameter `id` to retrieve that user's full details.

## Rules

- Include an `Authorization: Bearer <token>` header using one of the supported bearer token schemes.
- Support pagination using the `page` and `limit` query parameters as defined.
