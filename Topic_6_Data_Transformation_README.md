# Topic 6 Assessment - Data Transformation and Mapping

**Course:** n8n Hands-On Beginner Course  
**Workflow:** Manual Trigger -> Dirty Raw Data -> Reformat & Map  
**Purpose:** Standardize raw customer data using dynamic n8n expressions and output only the cleaned fields.

> **Documentation status:** This guide is based on the Topic 6 workflow instructions shared in the conversation and the provided final submission requirements. Actual execution, screenshots, export, GitHub URL, and video must be supplied by the learner. The full Topic 6 assessment text was not provided.

## 1. Objective

Create a three-node n8n workflow that trims leading and trailing spaces from name, email, and phone; converts the name to uppercase and the email to lowercase; and excludes the original raw fields from the final output.

## 2. Workflow structure

```text
Manual Trigger -> Dirty Raw Data (Edit Fields) -> Reformat & Map (Edit Fields)
```

## 3. Setup instructions

1. Create a new n8n workflow and save it with the name required by your Topic 6 assessment.
2. Add a **Manual Trigger** node.
3. Add an **Edit Fields (Set)** node and rename it **Dirty Raw Data**.
4. Set up three **String** fields in Dirty Raw Data. For the sample expected output below, use:

| Field | Example raw value |
|---|---|
| `Raw_Name` | `  jane doe  ` |
| `contact_email` | `  JANE@EXAMPLE.COM  ` |
| `phone_number` | `  123-456-7890  ` |

5. Execute Dirty Raw Data to confirm the three incoming fields are available.
6. Add another **Edit Fields (Set)** node, name it **Reformat & Map**, and choose **Manual Mapping**.
7. Turn **Include Other Input Fields** **OFF** so only the mapped clean fields remain.
8. Add the following three **String** fields. Set each value to **Expression**, not Fixed:

| Output field | Expression |
|---|---|
| `cleanName` | `{{ $json.Raw_Name.trim().toUpperCase() }}` |
| `cleanEmail` | `{{ $json.contact_email.trim().toLowerCase() }}` |
| `cleanPhone` | `{{ $json.phone_number.trim() }}` |

9. Click **Execute step** to test Reformat & Map, then **Test workflow** to run the complete workflow.
10. Open **Reformat & Map -> Output -> JSON** and verify the fields and values; then **Save**.

## 4. Expected final JSON

```json
[
  {
    "cleanName": "JANE DOE",
    "cleanEmail": "jane@example.com",
    "cleanPhone": "123-456-7890"
  }
]
```

The final output must not contain `Raw_Name`, `contact_email`, or `phone_number`. The exact result depends on the raw input values.

## 5. Validation and troubleshooting

- Confirm that all three nodes show successful execution indicators.
- Confirm each expression is evaluated; if literal `{{ ... }}` text appears, switch the value to **Expression** mode.
- If an expression fails, verify the input field spelling and that Dirty Raw Data ran successfully.
- If original fields remain, turn **Include Other Input Fields** OFF in Reformat & Map.
- `.trim()` removes whitespace at the beginning and end, not punctuation or spaces inside the string.

## 6. Evidence to capture

- Full workflow canvas with three connected nodes.
- Dirty Raw Data input field names, types, and values.
- Reformat & Map expressions and **Include Other Input Fields** OFF.
- Successful execution indicators and final JSON output.
- Execution history/log, if available in the n8n instance.

## 7. GitHub repository contents

```text
Topic6_Data_Transformation/
  README.md
  workflow.json                 # Actual export from n8n (not generated here)
  evidence/
    workflow-canvas.png
    raw-data.png
    reformat-and-map.png
    final-output.png
    execution-log.png
```

Export the actual workflow through the n8n workflow menu, and upload it along with this README and screenshots to a **public** GitHub repository. Do not substitute example JSON output for the workflow export.

## 8. LMS submission requirements

- **Mandatory:** Accessible Loom or YouTube demonstration showing expressions, successful execution, and final output.
- **Mandatory:** Public GitHub repository containing exported n8n workflow JSON, README, and supporting evidence.
- **Recommended:** LMS Description explaining challenges, resolutions, assumptions, limitations, or additional transformations.

## 9. Final submission checklist

- [ ] Completed all Topic 6 assessment exercises
- [ ] Verified the data-transformation workflow and final JSON output
- [ ] Exported the latest n8n workflow JSON and pushed it to GitHub
- [ ] Verified the GitHub repository is public and accessible
- [ ] Uploaded an accessible Loom/YouTube demonstration video
- [ ] Added relevant comments in the LMS Description field
- [ ] Reviewed all deliverables before submission

**Important:** Submissions missing the video, exported workflow source, or accessible public repository may be considered incomplete and may not be evaluated.
