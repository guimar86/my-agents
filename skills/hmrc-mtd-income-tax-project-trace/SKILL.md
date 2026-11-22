---
name: hmrc-mtd-income-tax-project-trace
description: Trace HMRC Making Tax Digital for Income Tax API calls in the current repository. Use when identifying implemented MTD Income Tax endpoints, tracing request flows, locating clients and DTOs, or validating MTD Income Tax integrations.
---

# MTD Income Tax Project Trace

## Objective

Identify and trace HMRC API integrations that
support Making Tax Digital for Income Tax.

## Scope

Only include integrations that can be established
as related to MTD Income Tax.

Do not include unrelated HMRC product integrations.

## Workflow

1. Search the repository for HMRC API clients.
2. Identify relevant MTD Income Tax base URLs
   and endpoint paths.
3. Locate HTTP client implementations.
4. Identify HTTP methods and API versions.
5. Identify authentication and OAuth scopes.
6. Locate request and response DTOs.
7. Trace calling application services.
8. Identify relevant integration tests.
9. Verify that the integration is related
   to MTD Income Tax.
10. Provide source file and line references.

## Trace

Where possible, follow:

MTD Income Tax feature
-> Application service
-> HMRC API client
-> HTTP request
-> Endpoint
-> Request and response models

## Output

Provide:

- API name
- Endpoint
- HTTP method
- API version
- Scope
- Business purpose
- Calling service
- Client class
- Request model
- Response model
- Source file and line references

Mark unknown values explicitly.

Do not claim that an API is executed at runtime
based only on static code analysis.

Do not modify project files.
