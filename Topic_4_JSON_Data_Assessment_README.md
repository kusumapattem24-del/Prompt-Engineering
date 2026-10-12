# Topic 4 Assessment — Working with JSON Objects, Arrays & Expressions

**Course:** N8N Hands-On Beginner Course  
**Workflow name:** `Topic4_JSON_Data_Assessment`  
**Architecture:** Manual Trigger → Mock Nested JSON Data (Code) → Extract Values (Edit Fields)

## Assessment Overview

This assessment evaluates the creation, inspection, transformation, and documentation of nested JSON in n8n using Manual Trigger, Code, and Edit Fields (Set) nodes.

## Objective

Demonstrate JSON objects and arrays, nested data navigation, dot notation, array index [0], expression-based extraction, type preservation, and final-output validation.

## Prerequisites

Review the Requirement Document, Implementation Plan, and Topic 4 Assessment. Complete Topics 1–3. Have an active n8n editor with Manual Trigger, Code, and Edit Fields nodes.

## Exercise 1 – Create and Name the Workflow

Create and save a new workflow named Topic4_JSON_Data_Assessment. Add Manual Trigger as the first node and connect subsequent nodes left to right.

## Exercise 2 – Generate Nested Customer JSON Data

Add a Code node named Mock Nested JSON Data. Generate a customer object containing an address object, an orders array with at least two orders, and a status or membership field. Execute and verify valid JSON.

### Example Code node payload (Run Once for All Items)

```javascript
return [
  {
    json: {
      customer: {
        name: "Jane Doe",
        email: "jane@example.com",
        address: { city: "New York", zipcode: "10001" }
      },
      orders: [
        { id: 101, total: 45.99 },
        { id: 102, total: 12.50 }
      ],
      status: "active"
    }
  }
];
```

## Exercise 3 – Inspect Objects, Arrays, and Data Types

Inspect the Code output in JSON, Table, and Schema views. Expand customer and orders; distinguish curly braces for objects and square brackets for arrays; confirm the first order is at index 0 and review displayed data types.

## Exercise 4 – Extract Nested Values Using Expressions

Add an Edit Fields (Set) node named Extract Values. Map customerName (String) from {{ $json.customer.name }}, cityOfCustomer (String) from {{ $json.customer.address.city }}, and firstOrderTotal (Number) from {{ $json.orders[0].total }}. Use Expression mode, not hardcoded values. Disable Include Other Input Fields to output only these three fields.

### Expected example output

```json
[
  {
    "customerName": "Jane Doe",
    "cityOfCustomer": "New York",
    "firstOrderTotal": 45.99
  }
]
```

## Exercise 5 – Execute, Validate, Document, and Submit

Execute the entire workflow and verify all nodes succeed. Confirm the final output contains exactly the three extracted fields with values matching the source. Save and export the workflow JSON, collect screenshots, prepare README and a public GitHub repository, record a Loom/YouTube demo, and submit the links in LMS.

## Success Criteria

Correct three-node sequence; valid nested JSON with objects, arrays and scalar fields; correct expression-based extraction; String/String/Number types; exactly three output fields; error-free execution; complete submission evidence.

## Required Deliverables

Mandatory: Loom/YouTube video link, public GitHub repository, exported n8n workflow JSON, README with setup/execution instructions, workflow and execution screenshots. Recommended: LMS description/comments. Optional: PDF/DOCX supporting documents.

## Submission Guidelines

Show nested JSON generation, JSON/Table/Schema inspection, expression configuration, successful execution and final output in the video. Publish the exported JSON, README and screenshots to a public GitHub repository. In LMS comments, document challenges, resolutions, assumptions, limitations and expression decisions.

## Important Note

Do not submit until the video and public repository are accessible and the actual exported workflow JSON and required screenshots are included. These documents are supporting documentation, not proof of execution.

## Practical Assessment Checklist

- [ ] Workflow named Topic4_JSON_Data_Assessment
- [ ] Manual Trigger connected to Mock Nested JSON Data and Extract Values
- [ ] Code node returns valid nested customer/address/orders JSON
- [ ] JSON, Table, and Schema views inspected
- [ ] All three expressions used with correct field types
- [ ] Final output has exactly three required fields
- [ ] Workflow executes successfully and is saved
- [ ] Workflow JSON exported
- [ ] Screenshots and README uploaded to public GitHub repository
- [ ] Loom/YouTube demonstration recorded and LMS links submitted

## Troubleshooting Notes

- Use **Run Once for All Items** for the sample Code node snippet.
- If fields are missing, inspect the Code node output and confirm field names and expression mode.
- If extra fields appear, turn off **Include Other Input Fields** in Extract Values.
- Ensure `firstOrderTotal` is Number rather than String.

## Evidence and Links (fill after execution)

- GitHub repository: _Add URL_
- Demonstration video: _Add URL_
- Workflow JSON: _Add file link_
- Screenshots: _Add folder link_
