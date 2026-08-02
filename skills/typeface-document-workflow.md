---
name: Run Typeface content approval workflows
description: Create documents with attached content workflows, move them
  through workflow steps, manage assignees, and search documents.
api: openapi/typeface-content-workflow-openapi.json
operations:
  - getWorkflows
  - getWorkflowsSteps
  - createDocument
  - addDocumentWorkflow
  - updateDocumentWorkflowStatusCopy
  - getDocumentAssignees
  - updateDocumentAssignees
  - getDocumentPdf
  - searchDocuments
generated: '2026-07-21'
method: generated
---

# Run Typeface content approval workflows

1. Authenticate (see `skills/typeface-generate-content.md`, step 1).
2. **Discover workflows.** `getWorkflows` lists a team's content workflows;
   `getWorkflowsSteps` returns the steps/statuses of one workflow.
3. **Create.** `createDocument` creates a new document with a content workflow
   attached, or bind a workflow to an existing document with
   `addDocumentWorkflow`.
4. **Advance.** `updateDocumentWorkflowStatusCopy` updates the workflow and/or
   status on a document — each transition fires a
   `document.workflow_state_changed` webhook (old/new step names and ids).
5. **Assign.** `getDocumentAssignees` / `updateDocumentAssignees` manage who
   owns the document at each step.
6. **Export & find.** `getDocumentPdf` exports the document;
   `searchDocuments` (Documents search & filter API,
   openapi/typeface-documents-search-openapi.json) searches within a project.

Webhook catalog: `asyncapi/typeface-webhooks.yml`. Errors:
`errors/typeface-problem-types.yml`.
