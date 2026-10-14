# Topic 13: IF Node & Conditional Logic

**Course:** N8N Hands-On Beginner Course  
**Document:** Step-by-Step Implementation Guide

## Objective
Build an n8n workflow that checks whether each customer's order value is at least 100, then routes qualifying orders to **VIP** and other orders to **Regular**.

## Workflow Structure

```text
Manual Trigger -> Mock Orders -> Check Order VIP Status (IF)
                                      | True  -> Set VIP
                                      | False -> Set Regular
```

## Step 1: Create a New Workflow
1. Log in to your n8n workspace and open **Workflows**.
2. Click **Add workflow**.
3. Name the workflow **Topic 13 IF Node Workflow**.
4. Click **Save**.

## Step 2: Configure Mock Orders
1. Add **When clicking 'Test workflow'** (Manual Trigger).
2. Add a **Code** node after the trigger and rename it **Mock Orders**. The implementation plan also allows Edit Fields (Set), but a Code node is a straightforward way to create two distinct items.
3. Set the Code node to **JavaScript** and **Run Once for All Items**.
4. Paste:

```javascript
return [
  { json: { customerName: "Alice", orderValue: 150 } },
  { json: { customerName: "Bob", orderValue: 75 } }
];
```

5. Click **Execute step**. Confirm **2 items** are returned.

## Step 3: Configure the IF Node
1. Add an **IF** node after Mock Orders.
2. Rename it **Check Order VIP Status**.
3. Add a condition with these settings:

| Setting | Value |
|---|---|
| Data type | Number |
| Value 1 | `{{ $json.orderValue }}` (Expression) |
| Operator | Is greater than or equal to |
| Value 2 | `100` |

4. Ensure `orderValue` is a **Number**, not a string. Execute the IF node and inspect both branches.

## Step 4: Add Downstream Actions

### True branch - VIP
1. Connect the **true** (upper) IF output to an **Edit Fields (Set)** node.
2. Rename it **Set VIP**.
3. Add `status` as a **String** with fixed value `VIP`.
4. Turn on **Include Other Input Fields** to preserve `customerName` and `orderValue`.

### False branch - Regular
1. Connect the **false** (lower) IF output to another **Edit Fields (Set)** node.
2. Rename it **Set Regular**.
3. Add `status` as a **String** with fixed value `Regular`.
4. Turn on **Include Other Input Fields** to preserve `customerName` and `orderValue`.

## Step 5: Execute and Verify
1. Click **Test workflow**.
2. Inspect the **Set VIP** node: Alice should be routed here.
3. Inspect the **Set Regular** node: Bob should be routed here.
4. Save the workflow.

### Expected output - Set VIP
```json
[
  { "customerName": "Alice", "orderValue": 150, "status": "VIP" }
]
```

### Expected output - Set Regular
```json
[
  { "customerName": "Bob", "orderValue": 75, "status": "Regular" }
]
```

## Validation Checklist
- [ ] Workflow saved as `Topic 13 IF Node Workflow`.
- [ ] Mock Orders generates two separate items.
- [ ] IF node uses numeric comparison `orderValue >= 100`.
- [ ] True output routes Alice (150) to VIP.
- [ ] False output routes Bob (75) to Regular.
- [ ] Both Set nodes preserve original fields and add `status`.
- [ ] Workflow completes without errors.

## Troubleshooting
- **Only one item appears:** Use the Code node example to return two separate n8n items.
- **Comparison fails:** Confirm `orderValue` is a number and Value 1 is in Expression mode.
- **Name or order value disappears:** Enable **Include Other Input Fields** in both Edit Fields nodes.
- **Wrong customer in branch:** Check the IF operator is **greater than or equal to** and the threshold is **100**.

## LMS Submission Evidence
Include the exported n8n workflow JSON, screenshots of both branch outputs, a GitHub repository link, and a demonstration video as required by your assessment.
