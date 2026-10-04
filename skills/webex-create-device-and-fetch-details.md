---
name: webex-create-device-and-fetch-details
description: Create a new device by MAC address and then retrieve its details.
api: openapi/webex-cloud-calling-openapi.yml
operations:
- CreateADeviceByMACAddress
- getDeviceDetails
generated: '2026-10-04'
method: generated
generator: extract-docs-artifacts.py skills (local)
source: openapi/webex-cloud-calling-openapi.yml ; every operationId checked against the contract
---

# webex-create-device-and-fetch-details

Create a new device by MAC address and then retrieve its details.

## Steps

1. 1. Use `CreateADeviceByMACAddress` with required body fields `macAddress` and optional fields `displayName`, `tags`.
2. 2. Use `getDeviceDetails` with path parameter `deviceId` returned from the create call.

## Rules

- Auth: Include a Bearer token in the `Authorization` header (e.g., `Authorization: Bearer <token>`).
- Errors: On failure, the API returns standard HTTP error codes; handle 4xx for client errors and 5xx for server errors.
