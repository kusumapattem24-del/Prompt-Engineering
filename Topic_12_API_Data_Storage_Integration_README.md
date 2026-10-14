# Topic 12: API & Data Storage Integration

**Course:** N8N Hands-On Beginner Course  
**Document type:** Implementation Plan / Step-by-Step Guide

## Overview
Combine an n8n HTTP Request node with Google Sheets to fetch external user data and store it in a spreadsheet. Learn standard and nested JSON field mapping and how n8n handles multiple incoming items.

## Workflow

`Manual Trigger -> Fetch API Users (HTTP Request) -> Store Users in Sheet (Google Sheets)`

## Step 1: Create a New Workflow
1. Open your n8n workspace and select **Workflows**.
2. Click **Add workflow**.
3. Rename it **Topic 12 API & Data Storage Integration Workflow**.
4. Click **Save**.

## Step 2: Prepare Your Google Sheet
1. Create a new spreadsheet in Google Sheets.
2. Name it **N8N API Storage Spreadsheet**.
3. Set row 1 headers exactly as follows:

| A1 | B1 | C1 | D1 |
|---|---|---|---|
| ID | Name | Email | Company |

4. Copy the Spreadsheet ID from the URL between `/d/` and `/edit`.
5. If using a Google service account, share the sheet with the service account email as **Editor**.

## Step 3: Add and Configure the HTTP Request GET Node
1. Add **When clicking 'Test workflow'** (Manual Trigger).
2. Connect an **HTTP Request** node.
3. Rename it **Fetch API Users**.
4. Configure:
   - **Method:** GET
   - **URL:** `https://jsonplaceholder.typicode.com/users`
   - **Authentication:** None
5. Click **Test step**.
6. Inspect the JSON output and confirm the API returns 10 user records with fields including `id`, `name`, `email`, and nested `company`.

## Step 4: Add the Google Sheets Append Row Node
1. Connect a **Google Sheets** node after **Fetch API Users**.
2. Rename it **Store Users in Sheet**.
3. Select your Google Sheets credential.
4. Configure:
   - **Resource:** Row
   - **Operation:** Append / Append Row
   - **Document:** N8N API Storage Spreadsheet (or Spreadsheet ID)
   - **Sheet:** Sheet1 (or your actual tab name)

## Step 5: Configure Dynamic and Nested Expressions
Map the spreadsheet columns using **Expression** mode:

| Google Sheets column | n8n expression |
|---|---|
| ID | `{{ $json.id }}` |
| Name | `{{ $json.name }}` |
| Email | `{{ $json.email }}` |
| Company | `{{ $json.company.name }}` |

The Company expression uses dot notation to access the `name` property inside the nested `company` object. Do not hardcode the company name.

## Step 6: Run and Verify the Entire Workflow
1. Click **Test workflow** on the canvas.
2. Confirm all three nodes succeed (Manual Trigger, Fetch API Users, Store Users in Sheet).
3. Open **N8N API Storage Spreadsheet**.
4. Verify 10 user rows have been appended, with ID, Name, Email, and Company populated.
5. Check the representative record: **Leanne Graham** should have **Romaguera-Crona** in Company.
6. Click **Save**.

> **Note:** n8n typically processes the 10 API results as 10 items within a node execution. The node may show “10 items” rather than 10 separate execution runs. Re-running the workflow can append duplicate rows; use a fresh sheet or clear prior test rows before final verification.

## Expected Result

| ID | Name | Email | Company |
|---|---|---|---|
| 1 | Leanne Graham | Sincere@april.biz | Romaguera-Crona |

**Success criteria:** 10 user rows appended with correct standard and nested field values, no workflow errors, and no unexpected duplicates during the assessed run.

## Submission Checklist
- [ ] Workflow saved with the required name
- [ ] GET request configured and tested
- [ ] Spreadsheet headers and credentials configured
- [ ] Four fields mapped dynamically
- [ ] Ten rows verified in Google Sheets
- [ ] Successful workflow execution screenshot captured
- [ ] Workflow JSON exported and README prepared
