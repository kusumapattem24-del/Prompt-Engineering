# Topic 14: Switch Node & Workflow Routing

**Course:** N8N Hands-On Beginner Course  
**Document:** Implementation Plan (Step-by-Step Guide)

## Objective
Use a Switch node to route four mock user profiles by role (admin, editor, viewer, guest), configure three equality rules and a fallback output, and assign access statuses using downstream Edit Fields nodes.

## Workflow Overview

`Manual Trigger -> Mock Users -> Route by Role (Switch)`

- **Output 0:** Set Admin -> `Admin Access`
- **Output 1:** Set Editor -> `Editor Access`
- **Output 2:** Set Viewer -> `Viewer Access`
- **Output 3 (fallback):** Set Guest -> `Guest Access`

## Step 1: Create a New Workflow
1. Log in to your n8n workspace and select **Workflows**.
2. Click **Add workflow**.
3. Rename the workflow **Topic 14 Switch Node Workflow**.
4. Click **Save**.

## Step 2: Configure Mock Users
1. Add **When clicking "Test workflow"** (Manual Trigger).
2. Add an **Edit Fields (Set)** node and name it **Mock Users**.
3. Prepare four *separate* items, one for each user. A **Code** node is a reliable alternative if your Edit Fields node cannot create multiple items from a JSON array.

### Sample user data (JSON)
```json
[
  {"username": "Alice", "role": "admin"},
  {"username": "Bob", "role": "editor"},
  {"username": "Charlie", "role": "viewer"},
  {"username": "Dave", "role": "guest"}
]
```

### Optional Code node (Run Once for All Items)
```javascript
return [
  { json: { username: 'Alice', role: 'admin' } },
  { json: { username: 'Bob', role: 'editor' } },
  { json: { username: 'Charlie', role: 'viewer' } },
  { json: { username: 'Dave', role: 'guest' } },
];
```

Execute the Mock Users or Code node and confirm **4 items** are present.

## Step 3: Configure the Switch Node
1. Connect **Mock Users** to a **Switch** node named **Route by Role**.
2. Select **Rules** mode (where available).
3. For each rule, use **String** comparison with **Value 1** as `{{ $json.role }}` and operator **is equal to**.
4. Create these rules **in order**:

| Rule | Value 2 | Output |
|---|---|---|
| 1 | `admin` | 0 |
| 2 | `editor` | 1 |
| 3 | `viewer` | 2 |

5. In **Options**, set **Fallback Output** to **Extra Output** (or the equivalent fallback setting). This creates **output 3** for unmatched roles such as `guest`.
6. Confirm the Switch node shows four output ports.

## Step 4: Add Downstream Nodes
Connect one Edit Fields (Set) node to each Switch output:

| Port | Node name | New String field | Value |
|---|---|---|---|
| 0 | Set Admin | `status` | `Admin Access` |
| 1 | Set Editor | `status` | `Editor Access` |
| 2 | Set Viewer | `status` | `Viewer Access` |
| 3 | Set Guest | `status` | `Guest Access` |

**Important:** Turn **Include Other Input Fields** ON in each Edit Fields node to retain the original `username` and `role` fields along with `status`.

## Step 5: Run and Verify
1. Click **Test workflow**.
2. Check that the Manual Trigger, mock-data node, Switch node, and all four destination nodes complete successfully.
3. Inspect each destination's output and confirm the results below.
4. Click **Save**.

| Username | Role | Routed node | Expected status |
|---|---|---|---|
| Alice | admin | Set Admin | Admin Access |
| Bob | editor | Set Editor | Editor Access |
| Charlie | viewer | Set Viewer | Viewer Access |
| Dave | guest | Set Guest | Guest Access |

## Troubleshooting
- **Only one item appears:** A JSON array inside one Edit Fields field may remain one item; use the optional Code node to emit four separate n8n items.
- **Guest has no output:** Set the Switch **Fallback Output** to **Extra Output** and connect the fourth port.
- **Original fields disappear:** Enable **Include Other Input Fields** in each destination node.
- **Wrong route:** Check exact lowercase role strings and the expression `{{ $json.role }}`.

## LMS Submission Checklist
- [ ] Saved workflow with all four branches
- [ ] Screenshot of Switch rules and fallback configuration
- [ ] Screenshot of four successful destination outputs
- [ ] Exported n8n workflow JSON
- [ ] GitHub repository / README link
- [ ] Demonstration video
