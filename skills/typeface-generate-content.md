---
name: Generate on-brand content with Typeface
description: Authenticate with application credentials, discover teams, pick or
  create a project, submit a batch content-generation request, poll the job,
  and fetch the generated document.
api: openapi/typeface-api-openapi.json
operations:
  - discoverIdentity
  - queryAccountsInOrg
  - queryProjectsInAccount_1
  - createProjectInAccount
  - getReadOnlyDocument
generated: '2026-07-21'
method: generated
---

# Generate on-brand content with Typeface

1. **Get a token.** POST `https://api-us.typeface.ai/oauth2/token`
   (`content-type: application/x-www-form-urlencoded`) with
   `grant_type=client_credentials`, `applicationId`, `applicationSecret`, and
   `tenantId` (your orgId). Tokens are JWTs valid for 60 minutes. Always use the
   global hostname for the token; use the team's datacenter hostname for
   everything else. Send `Authorization: Bearer <access_token>` on every other
   call.
2. **Discover context.** Call `discoverIdentity` to list the teams the app can
   access, or `queryAccountsInOrg` for teams by org. Responses follow the HAL
   model — follow returned links instead of hardcoding endpoints.
3. **Pick a project.** List with `queryProjectsInAccount_1` or create one with
   `createProjectInAccount`.
4. **Generate.** POST
   `/batch-service/accounts/{accountId}/projects/{projectId}/generate` with a
   `templates` array of generation requests (blog, email, social post, image;
   optionally brand kit, audience, layout).
5. **Poll.** GET
   `/batch-service/accounts/{accountId}/projects/{projectId}/batch-jobs/{monitorId}`
   until the job completes.
6. **Fetch output.** Call `getReadOnlyDocument` — the response contains an
   array of content blocks.

Errors use standard HTTP statuses with an `{"errorMessage", "status"}`
envelope; 429 means you are throttled — back off and retry. See
`errors/typeface-problem-types.yml` and `conventions/typeface-conventions.yml`.
