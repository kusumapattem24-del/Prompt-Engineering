# My First N8N Workflow

**Tayana Academy | N8N Hands-On Beginner | Topic 1: Create Your First Workflow**

## Assessment overview
Create, save, execute, and verify a basic n8n workflow. The workflow starts with a **Manual Trigger**, continues to an **Edit Fields (Set)** node, and returns a greeting as JSON.

## Objective
Demonstrate how to create and name a workflow, connect two nodes, configure a String field, run a manual test, and inspect the output in Table, JSON, and Schema views.

## Prerequisites
- Access to n8n version 1.0.0 or higher with workflow editing permissions.
- Browser access and ability to capture screenshots and record a demo.
- A public GitHub repository for the required LMS submission.

## Workflow architecture
`Manual Trigger (When clicking Execute workflow) -> Edit Fields (Set) -> JSON output`

## Configuration
1. Create a blank workflow and name it **My First N8N Workflow**.
2. Add **Manual Trigger** as the first node.
3. Connect **Edit Fields (Set)** after the trigger.
4. In Edit Fields, configure a field named `greeting` with String value `Hello, n8n!`. The demonstrated editor uses JSON mode with the same output.
5. Save and select **Execute workflow**.
6. Open the Edit Fields output and inspect Table, JSON, and Schema views.

## Expected JSON output
```json
{
  "greeting": "Hello, n8n!"
}
```

## Observed evidence
The screenshots shared during this assessment show the Manual Trigger and Edit Fields nodes connected with green success indicators. The Edit Fields output displays one item and the value `Hello, n8n!`; the workflow context displays the name **My First N8N Workflow**. Export, repository publication, and video submission have not yet been verified.

## Troubleshooting
- **No output:** Confirm the Manual Trigger is connected to Edit Fields and execute the workflow again.
- **Incorrect greeting:** Check the exact key `greeting` and value `Hello, n8n!` including capitalization and punctuation.
- **Cannot find results:** Open the Edit Fields node after a successful run and select the output view.

## LMS submission checklist
- [ ] Save the final workflow.
- [ ] Export the workflow as a `.json` file from n8n.
- [ ] Capture screenshots of the canvas, node settings, successful execution, and JSON output.
- [ ] Add this README and exported JSON to a public GitHub repository.
- [ ] Record and publish a Loom or YouTube demonstration (5-10 minutes is not specified by this assessment; show the complete run).
- [ ] Submit the public repository and demo links in LMS.

## Submission notes
Do not publish credentials, API keys, personal information, or private workspace URLs in public files or screenshots. This documentation describes the assessment workflow; it is **not** an exported n8n workflow JSON file.
