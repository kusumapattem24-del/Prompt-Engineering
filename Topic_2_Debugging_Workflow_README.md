# Topic 2 Assessment - Understanding Workflow Execution & Debugging Basics

**Course:** n8n Hands-On Beginner  
**Assessment:** Practical debugging workflow  
**Workflow name:** `Topic 2 Debugging Workflow`  
**Status:** Assessment guide; execution evidence must be captured from your own n8n workspace.

## 1. Assessment Overview

Build and debug a three-node workflow in n8n: **Manual Trigger -> Edit Fields (Set) -> HTTP Request**. Demonstrate an intentional HTTP failure, inspect the node input and error, correct the endpoint, test the HTTP Request node independently, and review failed and successful execution history.

## 2. Assessment Objective

Show that you can trace data between nodes, identify success/failure indicators, read error details and JSON, use **Test step**, and inspect historical executions.

## 3. Prerequisites

- Review the Requirement Document, Implementation Plan, and Topic 2 Assessment Document.
- Complete Topic 1 and have access to the n8n editor and **Executions** page.
- Have a GitHub account for publishing your exported workflow and documentation.

## 4. Workflow Architecture

`Manual Trigger -> Edit Fields (Set) -> HTTP Request (GET)`

The Edit Fields node must output:

```json
{
  "greeting": "Hello, n8n!"
}
```

**Intentional failure URL:** `https://this-domain-does-not-exist-12345.com`  
**Corrected URL:** Use the valid mock endpoint specified in your **Implementation Plan**. The endpoint was not supplied in this assessment text, so do not assume a particular URL.

## 5. Assessment Exercises

### Exercise 1 - Create and Prepare the Debugging Workflow

1. Open **My First N8N Workflow**.
2. Duplicate it and rename the copy **Topic 2 Debugging Workflow**.
3. Save it and verify the existing **Manual Trigger -> Edit Fields (Set)** connection.
4. Confirm the `greeting` field is exactly `Hello, n8n!`.

### Exercise 2 - Add and Trigger an Intentional Failure

1. Add an **HTTP Request** node after Edit Fields.
2. Set **Method = GET**.
3. Set **URL = https://this-domain-does-not-exist-12345.com**.
4. Execute the complete workflow.
5. Capture evidence showing the first two nodes succeeded and HTTP Request failed (red indicator).

### Exercise 3 - Inspect Input, Output, and Error Details

1. Open the failed **HTTP Request** node.
2. Inspect the **Input** panel; verify that the incoming item includes `greeting: Hello, n8n!`.
3. Inspect the **Output / Error** panel and error JSON.
4. Record the message, failed node, probable cause, available error code/name, and execution step.
5. Capture screenshots of the input and error details. Actual wording and codes depend on the n8n environment.

### Exercise 4 - Use Test Step and Verify Correction

1. Replace the invalid URL with the valid mock endpoint from the **Implementation Plan**.
2. Click **Test step** on the HTTP Request node.
3. Confirm that the HTTP Request node succeeds and inspect its response.
4. Explain the distinction: **Test step** executes a selected node with available input; **Test workflow** starts the workflow execution from its trigger.
5. Execute the complete corrected workflow as well so that successful workflow history is available.

### Exercise 5 - Review Execution History and Prepare Submission

1. Open **Executions** and find the failed and successful runs.
2. Open a historical run and inspect status, date/time, duration, inputs, outputs, and errors where available.
3. Export the completed workflow as `.json`.
4. Prepare the README and evidence screenshots.
5. Record the Loom/YouTube demo and publish the source and documentation in a public GitHub repository.

## 6. Debugging Observation Record

| Item | What to record |
|---|---|
| Failed node | HTTP Request |
| Request method | GET |
| Failed URL | `https://this-domain-does-not-exist-12345.com` |
| Incoming input | `{"greeting":"Hello, n8n!"}` |
| Error message / code | Fill in from your actual failed execution |
| Likely cause | Invalid / unresolvable test domain (confirm against actual error) |
| Corrected endpoint | Fill in the URL from your Implementation Plan |
| Corrected response | Fill in from the successful Test step |
| Failed / successful execution IDs | Fill in from n8n execution history |

## 7. Test Step vs Test Workflow

| Test step | Test workflow |
|---|---|
| Runs the selected node with available input data. | Runs the workflow from its trigger. |
| Useful for checking one node after changing its configuration. | Useful for verifying the full connected process. |
| Does not, by itself, prove the full workflow succeeds. | Confirms end-to-end behavior when all nodes complete. |

## 8. Practical Assessment Checklist

- [ ] Duplicated Topic 1 and saved **Topic 2 Debugging Workflow**.
- [ ] Connected Manual Trigger -> Edit Fields -> HTTP Request.
- [ ] Executed the invalid GET request and captured the red error indicator.
- [ ] Verified incoming greeting in the HTTP Request Input panel.
- [ ] Captured the Output/Error panel and error JSON.
- [ ] Documented error message, cause, code/name, and step where available.
- [ ] Replaced the URL with the Implementation Plan's valid mock endpoint.
- [ ] Ran **Test step** and inspected successful output.
- [ ] Ran the full corrected workflow and inspected both execution histories.
- [ ] Exported the actual workflow JSON and prepared README and screenshots.
- [ ] Published the public GitHub repository and demo video.

## 9. Required Deliverables

| Deliverable | Requirement |
|---|---|
| Loom / YouTube demonstration video link | Mandatory |
| Public GitHub repository link | Mandatory |
| Exported n8n workflow `.json` or source file | Mandatory |
| README with setup and debugging evidence | Mandatory |
| LMS description / additional comments | Recommended |
| Supporting screenshots or PDF/DOCX | Optional |

## 10. Suggested GitHub Repository Layout

```text
n8n-topic-2-debugging/
  README.md
  Topic_2_Debugging_Workflow.json     # export this from n8n
  evidence/
    workflow-failed.png
    http-input.png
    http-error.png
    http-test-step-success.png
    execution-history.png
```

## 11. Suggested LMS Description

Created a three-node n8n debugging workflow by duplicating the Topic 1 workflow. Intentionally configured an invalid HTTP Request URL, inspected the failing node's input and error details, then corrected the URL using the endpoint from the Implementation Plan. Verified the HTTP Request with Test step and reviewed failed and successful executions in history. Workflow export, README, evidence, and demonstration are provided in the linked repository and video. Replace this template with the exact error and any challenges observed during your run.

## 12. Final Submission Verification

- [ ] Video shows the failed run, error JSON, corrected Test step, and execution history.
- [ ] Repository is public and contains the **actual** exported workflow JSON.
- [ ] README and screenshots are readable and accurately reflect real executions.
- [ ] Links work without special access.
- [ ] LMS comments include the real error, diagnosis, correction, and any limitations.

**Important:** This document is a guide based on the supplied Topic 2 assessment. It does not constitute proof that the workflow was run, and the valid mock URL cannot be supplied without the referenced Implementation Plan.
