# Topic 8: Webhook Trigger

**Requirement Document | N8N - Hands On Beginner Course**

## 1. Document Control

| Field | Value |
|---|---|
| Document Title | Requirement Document: Topic 8 - Webhook Trigger |
| Course | N8N - Hands On Beginner Course |
| Target Audience | Trainee / Employee |
| Version | 1.0 |
| Status | Approved |
| Last Updated | June 24, 2026 |

## 2. Objectives & Scope

### 2.1 Course Objective
Teach trainees and employees to configure the Webhook Trigger node to receive external data and capture incoming HTTP requests. Learners distinguish Test and Production Webhook URLs, activate listening in n8n, and inspect and process the incoming JSON request body.

### 2.2 Learning Scope

**In scope**
- Add and configure a Webhook trigger on the canvas.
- Set HTTP Method to `POST` and Path to `contact-form`.
- Locate, copy, and distinguish Test and Production URLs.
- Activate listening mode to capture a test payload.
- Send mock JSON with `name`, `email`, and `message`; inspect the request body.
- Connect an Edit Fields (Set) node named `Process Webhook Data` to map incoming attributes.

**Out of scope**
- Custom webhook responses, custom headers, status codes, or response JSON.
- Authentication such as Basic Auth, Header Auth, or JWT validation.
- Binary/file uploads or multipart form data.

## 3. Target Audience Requirements (Prerequisites)

- Complete Topics 1 through 7.
- Understand basic HTTP methods (GET and POST) and JSON format.
- Have an HTTP client such as curl, Postman, or a web-based client able to send JSON POST requests.

## 4. Functional Requirements

| ID | Section | Requirement | Priority |
|---|---|---|---|
| REQ-001 | Webhook Node Setup | Start with a Webhook node accepting HTTP POST on `contact-form`. | High |
| REQ-002 | URL Differentiator | Use Test URL for development; understand that Production URL requires activation. | High |
| REQ-003 | Webhook Payload Capture | Capture and display `name`, `email`, and `message` from incoming JSON body. | High |
| REQ-004 | Data Mapping | `Process Webhook Data` maps `body.name` to `customerName`, `body.email` to `customerEmail`, and `body.message` to `customerMessage`. | High |
| REQ-005 | Payload Cleanup | Exclude metadata (headers, query, context); output only three flat mapped keys. | High |
| REQ-006 | Complete Testing | Complete without errors when valid JSON POST reaches Test URL while n8n listens. | High |

## 5. Technical Requirements

| ID | Technical Requirement | Details |
|---|---|---|
| TR-001 | Webhook Server Listener | n8n exposes a network-accessible endpoint routing HTTP requests to the correct workflow trigger. |
| TR-002 | JSON Parser | n8n parses `application/json` and places request data under `$json.body`. |
| TR-003 | Editor UI Listener State | n8n editor supports a listening state (e.g., 120-second countdown) to capture and display the incoming request. |

## 6. Stakeholders and Personas

| Persona | Role | Need |
|---|---|---|
| Trainee / Employee | Student | Learn to integrate n8n with external systems (form builders, CRM alerts, applications) using webhook endpoints. |
| Instructor / Reviewer | Evaluation | Verify correct method/path, test listener usage, and dynamic JSON body mapping. |

## 7. Assumptions & Constraints

- **ASM-001:** The n8n instance is reachable from the trainee's HTTP client, locally or over the internet when externally hosted.
- **ASM-002:** The test request contains valid JSON with the correct keys.
- **CON-001:** The Test Webhook URL works only while `Listen for test event` is active and times out after approximately 120 seconds if no request arrives.

## Reference Workflow Configuration

`Webhook (POST /contact-form) -> Process Webhook Data (Edit Fields / Set)`

Set **Include Other Input Fields = Off** in `Process Webhook Data`.

| Output field | Type | Expression |
|---|---|---|
| `customerName` | String | `{{ $json.body.name }}` |
| `customerEmail` | String | `{{ $json.body.email }}` |
| `customerMessage` | String | `{{ $json.body.message }}` |

**Sample test body**

```json
{
  "name": "Alice Smith",
  "email": "alice@example.com",
  "message": "Hello from webhook!"
}
```

**Expected mapped output (when sample input is used)**

```json
{
  "customerName": "Alice Smith",
  "customerEmail": "alice@example.com",
  "customerMessage": "Hello from webhook!"
}
```

## Validation and Evidence

1. Confirm Webhook node uses `POST` and path `contact-form`.
2. Select the **Test URL**, then click **Listen for test event**.
3. Send a valid `application/json` POST request to the exact Test URL shown by n8n.
4. Inspect Webhook output and expand `body` to verify the three input fields.
5. Confirm `Process Webhook Data` has the three dynamic expressions and excludes original input fields.
6. Inspect final JSON output and verify only the three clean fields remain.
7. Capture screenshots and export the actual workflow JSON from n8n for assessment evidence.

**Evidence note:** This document describes the required configuration and expected results. It does not certify that a live workflow was executed or that screenshots were captured.
