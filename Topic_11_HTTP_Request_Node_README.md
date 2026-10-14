# Topic 11: HTTP Request Node — Implementation Guide

**Course:** N8N Hands-On Beginner Course  
**Workflow name:** `Topic 11 HTTP Request Node Workflow`  
**Purpose:** Retrieve mock user data with GET, transform it dynamically, and submit it with POST.

## Workflow structure

`Manual Trigger → Fetch User (HTTP GET) → Prepare Post Payload (Edit Fields) → Send Custom Post (HTTP POST)`

## Step 1 — Create and save the workflow

1. Log in to your n8n workspace and open **Workflows**.
2. Select **Add workflow**.
3. Name it **Topic 11 HTTP Request Node Workflow** and click **Save**.

## Step 2 — Fetch user data with GET

1. Add **Manual Trigger** (`When clicking "Test workflow"`).
2. Add **HTTP Request** after it and rename it **Fetch User**.
3. Configure **Method: GET**, **URL: `https://jsonplaceholder.typicode.com/users/1`**, **Authentication: None**.
4. Click **Test step** and inspect **OUTPUT → JSON**. Confirm that `id`, `name`, `username`, and `email` are present.

## Step 3 — Prepare the POST payload

1. Add **Edit Fields (Set)** after Fetch User. Rename it **Prepare Post Payload**.
2. Set **Mode: Manual Mapping**. Add two **String** fields:

| Field | Value (Expression mode) |
|---|---|
| `title` | `User Post by {{ $json.name }}` |
| `body` | `Email: {{ $json.email }}` |

3. Set **Include Other Input Fields** to **Off** to keep only the mapped fields (optional cleanup).
4. Click **Test step**. With the sample API response, expect:

```json
{
  "title": "User Post by Leanne Graham",
  "body": "Email: Sincere@april.biz"
}
```

## Step 4 — Send the POST request

1. Add a second **HTTP Request** after Prepare Post Payload. Rename it **Send Custom Post**.
2. Configure the node:

| Setting | Value |
|---|---|
| Method | `POST` |
| URL | `https://jsonplaceholder.typicode.com/posts` |
| Authentication | `None` |
| Send Body | `On` |
| Body Content Type | `JSON` |
| Specify Body | `Using Fields Below` |
| Body field `title` | `{{ $json.title }}` (Expression) |
| Body field `body` | `{{ $json.body }}` (Expression) |

3. Test the node and check that the request uses the preceding node's output, not hardcoded strings.

## Step 5 — Execute and verify

1. Click **Test workflow** to run all four nodes.
2. Confirm successful indicators for Manual Trigger, Fetch User, Prepare Post Payload, and Send Custom Post.
3. Open **Send Custom Post → OUTPUT → JSON**. The mock response should resemble:

```json
{
  "title": "User Post by Leanne Graham",
  "body": "Email: Sincere@april.biz",
  "id": 101
}
```

4. Click **Save**.

**Important:** JSONPlaceholder simulates POST creation; it does not permanently save a real post. The response `id` is typically `101`, but check the actual response in your execution.

## Troubleshooting

- **No input fields in Prepare Post Payload:** Run **Fetch User** first and verify its JSON response.
- **Expression appears literally:** Switch the value box to **Expression** mode; verify the preview resolves the name/email.
- **POST body missing:** Enable **Send Body**, choose **JSON**, and add both named fields.
- **HTTP request fails:** Check the URL, internet access, request method, and error details in the node output.
- **Different output:** Validate against the actual live API response rather than assuming the sample data never changes.

## Evidence and submission notes

Capture screenshots of the complete workflow, GET settings and JSON output, Edit Fields expressions and mapped output, POST settings, and successful final response. Export the workflow as JSON using n8n's workflow menu and place it in your GitHub repository alongside this README and evidence. Add your demonstration video link if required by your LMS assessment.

**Evidence status:** This guide describes expected behavior; it does not claim that the workflow has been executed or verified in your n8n instance.
