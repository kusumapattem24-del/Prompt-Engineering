# Topic 15: Split in Batches & Basic Error Handling

**Course:** N8N Hands-On Beginner Course  
**Document:** Implementation Plan - Step-by-Step Guide

## Objective
Use the Split in Batches (Loop Over Items) node to process five URLs in groups of two. Configure an HTTP Request node to continue after an invalid URL, complete all batches, and run a final Done-branch node.

## Workflow

`Manual Trigger -> Mock Items List -> Split in Batches (Loop Over Items)`

- **Loop output -> Fetch Details (HTTP Request) -> back to Split in Batches input**
- **Done output -> Compile Final List (Edit Fields)**

> **Version note:** In current n8n versions, the node is often named **Loop Over Items** (formerly Split in Batches). Its **Done** output is generally the top port and **Loop** the bottom port. Follow the output labels shown in your editor rather than assuming the port position.

## Step 1 - Create a New Workflow
1. Log in to your n8n workspace and select **Workflows > Add workflow**.
2. Name it **Topic 15 Split in Batches Workflow**.
3. Save the workflow.

## Step 2 - Configure Mock Items List
1. Add **Manual Trigger** as the starting node.
2. Add a **Code** node after it, and rename it **Mock Items List**. A Code node is a reliable way to produce five separate n8n items; an Edit Fields node containing one JSON array does not necessarily create five items.
3. Set **Run Once for All Items** and paste:

```javascript
return [
  { json: { url: 'https://jsonplaceholder.typicode.com/posts/1' } },
  { json: { url: 'https://jsonplaceholder.typicode.com/posts/1' } },
  { json: { url: 'https://invalid-url-domain-does-not-exist.xyz/' } },
  { json: { url: 'https://jsonplaceholder.typicode.com/posts/1' } },
  { json: { url: 'https://jsonplaceholder.typicode.com/posts/1' } }
];
```

4. Execute the node and verify **5 items** appear in its output.

## Step 3 - Add Split in Batches
1. Add **Loop Over Items** (also called **Split in Batches**) after Mock Items List.
2. Set **Batch Size = 2**.
3. Locate the labeled **Loop** and **Done** outputs.
4. Expect three batches: **2 items, 2 items, 1 item**.

## Step 4 - Add HTTP Request inside the Loop
1. Connect the **Loop** output to an **HTTP Request** node named **Fetch Details**.
2. Set **Method = GET** and **Authentication = None**.
3. Set the **URL** to Expression mode: `{{ $json.url }}`.
4. Verify the preview resolves to the incoming item's URL, not a fixed address.

## Step 5 - Configure Error Handling
1. Open **Fetch Details > Settings**.
2. Under **On Error**, choose **Continue** (or **Continue on Fail** in older versions).
3. For clear error details, select **Continue (using error output)** if available and route the error output back to the loop as well; otherwise use Continue so the failed item does not stop the workflow.
4. Save the node.

## Step 6 - Connect the Feedback Loop
1. Connect the **Fetch Details** regular output back to the **input** of Split in Batches / Loop Over Items.
2. If using a separate error output, connect that path back to the loop input too (merge branches if needed).
3. Confirm that the loop repeats until all five input items have been attempted.

## Step 7 - Add the Done Branch
1. From the **Done** output, add an **Edit Fields (Set)** node.
2. Rename it **Compile Final List**.
3. Add a String field **status** with fixed value **All Batches Processed**.
4. If you need to retain existing fields, enable **Include Other Input Fields**.

## Step 8 - Run and Verify
1. Click **Test workflow**.
2. Confirm that batches are processed in order **2 + 2 + 1**.
3. The third item uses an intentionally invalid URL; its HTTP request should produce error information, but processing should continue.
4. Confirm the fourth and fifth items are attempted and the **Done** branch executes.
5. Inspect **Compile Final List** and verify the `status` value.
6. Save the workflow.

## Expected Results

| Check | Expected result |
|---|---|
| Input count | 5 separate items |
| Batch size | 2 |
| Batch iterations | 3 (2, 2, 1) |
| Invalid request | Item 3 fails without terminating the workflow |
| Completion | Done branch runs after the loop finishes |
| Final status | `All Batches Processed` |

## Troubleshooting
- **Only one item enters the loop:** Make sure the mock node returns five separate n8n items, not one item containing an array.
- **Workflow stops on bad URL:** Check **Fetch Details > Settings > On Error** and reconnect any error output to the loop.
- **Done branch does not execute:** Check the feedback connection and that the HTTP node returns output on failure.
- **Port positions differ:** Use the **Loop** and **Done** labels in your n8n version.
- **Repeated test runs:** This exercise uses GET requests, so it does not create posts on JSONPlaceholder.

## Submission Evidence
- Screenshot of the complete workflow and feedback loop.
- Mock Items List output showing five items.
- Split in Batches setting showing batch size 2.
- HTTP Request settings showing dynamic URL and error continuation.
- Execution evidence of the failed URL, later successful requests, and Done branch.
- Exported workflow JSON and demonstration recording (if required by the assessment).
