# Topic 9: Google Sheets Integration

**Course:** N8N Hands-On Beginner Course  
**Document:** Implementation Plan and GitHub README  
**Workflow name:** `Topic 9 Google Sheets Integration Workflow`

## Objective
Connect n8n to Google Sheets to append a mock customer, read spreadsheet rows, and update the customer's status from `Pending` to `Verified` using dynamic field mapping.

## Workflow structure

`Manual Trigger -> Mock Customer Data -> Append Customer Row -> Read Customers -> Update Customer Status`

## Step 1 - Create the workflow
1. Sign in to n8n and open **Workflows**.
2. Select **Add workflow**.
3. Name it `Topic 9 Google Sheets Integration Workflow` and **Save**.

## Step 2 - Configure mock customer data
1. Add **Manual Trigger** (When clicking Test workflow).
2. Connect an **Edit Fields (Set)** node named `Mock Customer Data`.
3. Under **Fields to Set**, create two **String** fields:

| Field | Type | Fixed value |
|---|---|---|
| `customerName` | String | `Charlie Brown` |
| `customerEmail` | String | `charlie@example.com` |

4. Click **Test step** and check the output:

```json
[
  {
    "customerName": "Charlie Brown",
    "customerEmail": "charlie@example.com"
  }
]
```

## Step 3 - Prepare the spreadsheet
1. In Google Sheets, create a spreadsheet named `N8N Test Spreadsheet`.
2. In the first row of `Sheet1`, enter the exact headers **Name**, **Email**, and **Status**.
3. Copy the spreadsheet ID from the URL between `/d/` and `/edit`.
4. If authenticating with a service account, share the spreadsheet with that service-account email as **Editor**. Otherwise select the appropriate Google Sheets credentials in n8n.

## Step 4 - Append a customer row
1. Add a **Google Sheets** node after `Mock Customer Data`, named `Append Customer Row`.
2. Select your Google Sheets credential; Resource **Row**; Operation **Append** / **Append Row**.
3. Choose the spreadsheet ID (or `N8N Test Spreadsheet`) and `Sheet1`.
4. Map the columns:

| Sheet column | Mapping | Mode |
|---|---|---|
| Name | `{{ $json.customerName }}` | Expression |
| Email | `{{ $json.customerEmail }}` | Expression |
| Status | `Pending` | Fixed |

5. Click **Test step** and confirm the row appears in Google Sheets.

## Step 5 - Read customer rows
1. Add another Google Sheets node named `Read Customers`.
2. Select the same credential, Resource **Row**, Operation **Read** / **Read Rows** (some versions show **Get Row(s)**).
3. Select the same spreadsheet and `Sheet1`.
4. Test the node and inspect its JSON output to verify the appended customer row is returned.

## Step 6 - Update customer status
1. Add a third Google Sheets node named `Update Customer Status`.
2. Select the same credential, Resource **Row**, Operation **Update** / **Update Row**.
3. Select the same spreadsheet and `Sheet1`.
4. Set the matching/lookup column to **Email** and set the value to the email from the incoming item.
5. Set **Status** to the fixed value `Verified`.

**Important mapping note:** The Implementation Plan specifies `{{ $json.customerEmail }}` as the lookup value. However, after **Read Customers**, incoming items often use the sheet's column names (such as `Email`) rather than `customerEmail`. Inspect the actual `Read Customers` output. If it contains `Email`, use `{{ $json.Email }}` or map the original value from the earlier node. In n8n versions using **Update Row**, set **Email (using to match)** to the incoming email and **Status** to `Verified`.

## Step 7 - Run and validate
1. Click **Test workflow** to run the entire chain.
2. Verify all nodes complete successfully.
3. Open `N8N Test Spreadsheet` and find the row where **Email** equals `charlie@example.com`.
4. Confirm the row's **Status** is now `Verified`.
5. Click **Save**.

### Expected spreadsheet row

| Name | Email | Status |
|---|---|---|
| Charlie Brown | charlie@example.com | Verified |

## Troubleshooting and practical notes
- **No sheet available:** Check the credential, spreadsheet ID, tab name, and spreadsheet sharing permissions.
- **Columns missing:** Ensure the header row uses `Name`, `Email`, and `Status` exactly; refresh the column mapping.
- **Update fails to find the row:** Check whether the incoming item has `Email` or `customerEmail`; use the field actually present in the input JSON.
- **Repeated testing:** Running the full workflow again can append another row for the same email. Clear duplicate test rows or reset the sheet before an assessed run.
- **Data privacy:** Use the provided mock customer information, not real customer details, in public evidence.

## Evidence and LMS/GitHub submission
Capture screenshots of the workflow canvas, mock input output, Google Sheets append mapping, read output, update mapping, final spreadsheet row, and successful execution. Export the **actual** workflow JSON from n8n and include it alongside this README in a GitHub repository. Add your Loom/YouTube demonstration link and any implementation observations. This README is documentation; it is **not** an exported executable n8n workflow.

## Completion checklist
- [ ] Workflow saved with the correct name
- [ ] Mock Customer Data has both String fields
- [ ] Google Sheets credential and spreadsheet configured
- [ ] Append Customer Row adds a `Pending` row
- [ ] Read Customers returns the appended row
- [ ] Update Customer Status changes it to `Verified`
- [ ] Full workflow executes successfully
- [ ] Screenshots, exported workflow JSON, README, and demo prepared
