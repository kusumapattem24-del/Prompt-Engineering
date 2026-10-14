# Topic 10: Gmail Integration

**Course:** N8N Hands-On Beginner Course  
**Document:** Implementation Plan and GitHub README  
**Workflow name:** `Topic 10 Gmail Integration Workflow`

## Objective
Connect n8n to Gmail and send a personalized email using a recipient name and email address supplied by an earlier Edit Fields node. Verify that the recipient, subject, and message body are populated dynamically.

## Workflow structure
`Manual Trigger -> Mock Customer Data (Edit Fields) -> Send Personalized Email (Gmail)`

## Prerequisites
- Access to an n8n workspace and a Google account authorized for Gmail sending.
- A Gmail OAuth2 credential in n8n. Depending on the instance, an administrator may need to configure Google OAuth client credentials and the callback URL.
- A test inbox you can access. Use your own address rather than sending test messages to an unknown recipient.

## Step 1 - Create the workflow
1. Open **Workflows > Add workflow**.
2. Name it **Topic 10 Gmail Integration Workflow**.
3. Click **Save**.

## Step 2 - Configure mock customer data
1. Add **Manual Trigger** (When clicking Test workflow).
2. Add **Edit Fields (Set)** and rename it **Mock Customer Data**.
3. In **Manual Mapping**, create two **String** fields:

| Field | Type | Value |
|---|---|---|
| `customerName` | String | `Alice Smith` |
| `customerEmail` | String | An email address you own or can access |

4. Click **Execute step** to confirm both fields appear in the output.

Example input (replace the email with your own test inbox):

```json
{
  "customerName": "Alice Smith",
  "customerEmail": "your-test-inbox@example.com"
}
```

## Step 3 - Configure Gmail credentials
1. In the Gmail node or **Credentials**, select an existing **Gmail OAuth2** credential or create one.
2. Follow the Google authorization process and confirm the credential connects successfully.
3. Do not publish client secrets, OAuth tokens, or credential exports to GitHub.

## Step 4 - Add the Gmail send node
1. Add **Gmail** after **Mock Customer Data**.
2. Rename it **Send Personalized Email**.
3. Choose the authorized Gmail credential.
4. Set **Resource = Message** and **Operation = Send**.

## Step 5 - Configure dynamic expressions

| Gmail field | Setting |
|---|---|
| To | `{{ $json.customerEmail }}` |
| Subject | `Welcome to N8N Course, {{ $json.customerName }}!` |
| Email Type | Plain Text |

**Message body:**

```text
Hi {{ $json.customerName }},

Congratulations on completing Topic 10 of the N8N Hands-On Beginner Course!
This personalized email was sent automatically using dynamic content from a previous node.

Best regards,
Your Automation Engine
```

Set the recipient field to **Expression** mode. For subject and body, use n8n's supported inline-expression handling and check the preview resolves `customerName` correctly.

## Step 6 - Execute and verify
1. Click **Test workflow**.
2. Verify all three nodes finish successfully.
3. Open the test inbox and check the email arrived.
4. Confirm the subject reads **Welcome to N8N Course, Alice Smith!** and the greeting reads **Hi Alice Smith,**.
5. Click **Save**.

**Important:** A green Gmail node indicates the send request succeeded; actual inbox delivery should be checked separately (including Spam/Junk if necessary).

## Troubleshooting
- **No credential / OAuth error:** Confirm Google authorization and that the OAuth callback URL matches your n8n instance configuration.
- **Recipient is blank:** Execute Mock Customer Data and check `customerEmail` spelling and expression mode.
- **Literal `{{ ... }}` in email:** Switch to expression-aware input and verify the preview.
- **No email in inbox:** Check the Gmail node result, recipient address, and spam folder. Avoid repeated tests until you know whether a message was sent.

## Evidence and LMS / GitHub submission
- [ ] Screenshot: workflow canvas and node names
- [ ] Screenshot: Mock Customer Data input and output (hide personal addresses if necessary)
- [ ] Screenshot: Gmail Message / Send configuration (hide credentials)
- [ ] Screenshot: successful execution
- [ ] Screenshot: received email with personalized subject and greeting
- [ ] Exported workflow JSON (without secrets)
- [ ] Public GitHub repository with this README, workflow JSON, and evidence
- [ ] Loom / YouTube demonstration link, if required by your assessment

## Notes
This document describes the provided implementation plan. It is not evidence that the workflow has been executed or that an email has been delivered. Actual screenshots, the exported n8n workflow, and demonstration links must be added after testing.
