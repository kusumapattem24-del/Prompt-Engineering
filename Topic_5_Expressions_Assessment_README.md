# Topic 5 Assessment - Expressions & Variables

**n8n Hands-On Beginner Course | Assessment documentation and GitHub README**

> This document follows the supplied Topic 5 assessment. Execution, screenshots, video and repository publication must be completed by the learner.

## Workflow at a glance

`Manual Trigger -> Generate Employee Data -> Process Expressions`

**Assessment workflow name:** `Topic5_Expressions_Assessment`

## Setup and execution

1. Create a workflow with the exact assessment name and save it.
2. Add Manual Trigger.
3. Add an Edit Fields (Set) node named **Generate Employee Data**. In Manual Mapping, create String fields `firstName = john`, `lastName = smith`, `birthDate = 1998-04-12T08:30:00Z`. Test the node.
4. Add a second Edit Fields (Set) node named **Process Expressions**. Configure the three String fields below in **Expression** mode, not Fixed mode.
5. Optionally enable **Include Other Input Fields** to retain the source fields.
6. Run **Test workflow**, inspect the final node's JSON output, and save.
7. Export the workflow from n8n as JSON; add it and real screenshots to a public GitHub repository. Record and submit a Loom/YouTube demo.

## Required expressions

| Field | Type | Expression | Expected result |
|---|---|---|---|
| `fullNameUpperCase` | String | `{{ ($json.firstName + ' ' + $json.lastName).toUpperCase() }}` | `JOHN SMITH` |
| `formattedBirthDate` | String | `{{ $dateTime.fromISO($json.birthDate).toFormat('MMMM dd, yyyy') }}` | `April 12, 1998` |
| `processedDate` | String | `{{ $now.toFormat('yyyy-MM-dd') }}` | Actual execution date |

**Compatibility note:** If your n8n version does not expose `$dateTime.fromISO`, use `{{ DateTime.fromISO($json.birthDate).toFormat('MMMM dd, yyyy') }}` as a Luxon-based alternative, then verify the result.

## Expected transformed JSON

```json
[
  {
    "fullNameUpperCase": "JOHN SMITH",
    "formattedBirthDate": "April 12, 1998",
    "processedDate": "<actual execution date in yyyy-MM-dd format>"
  }
]
```

The placeholder for `processedDate` is illustrative, not literal JSON to submit. When **Include Other Input Fields** is enabled, the original `firstName`, `lastName`, and `birthDate` fields may also appear.

## Evidence and LMS submission

- [ ] Workflow and node configuration screenshots
- [ ] Successful run and JSON output screenshots
- [ ] Execution history screenshot
- [ ] Actual exported n8n workflow JSON file
- [ ] Public GitHub repository with this README and evidence
- [ ] Accessible Loom/YouTube demonstration link
- [ ] LMS description covering challenges, resolutions, assumptions and timezone considerations

## Assessment source text

The following is the supplied Topic 5 assessment text (HTML entities decoded for readability).

---

Topic 5 Assessment
Expressions & Variables
1. Assessment Overview
This assessment evaluates your ability to build, execute, verify, and document an n8n
workflow that uses dynamic expressions and variables to transform employee profile data.
You will configure input fields, combine strings, convert text to uppercase, parse and format
an ISO date, generate the current processing date, validate the final JSON output, and
prepare complete LMS submission evidence. The assessment is based on the provided
Requirement Document, Implementation Plan, and original milestone assessment.
2. Assessment Objective
Demonstrate your ability to use n8n expression syntax to reference values dynamically,
concatenate first and last names, apply JavaScript text methods, parse ISO date strings with
the built-in $dateTime helper, format dates using Luxon toFormat() tokens, and retrieve the
current date through the global $now variable. The completed workflow must run
successfully and produce the required output without hardcoded transformed values.
3. Prerequisites
-  Review the Requirement Document before starting the assessment.
-  Review the Implementation Plan for the recommended workflow configuration and
execution sequence.
-  Complete Topic 1 through Topic 4 of the n8n Hands-On Beginner learning path.
-  Have access to an active n8n editor session with expression capabilities enabled.
-  Understand basic JSON key-value structures and introductory JavaScript operations
such as concatenation and method calls.
-  Have a GitHub account available for public workflow source and documentation
submission.
4. Assessment Tasks
Assessment Material
Topic 5: Expressions & Variables
Assessment Scenario: Process employee profile data received from an HR system. Create an
uppercase full name, convert the employee's ISO birth date into a readable format, and
dynamically generate the date on which the workflow is processed.
Workflow Structure: Manual Trigger  ->  Edit Fields (Generate Employee Data)  ->  Edit Fields
(Process Expressions)
Exercise 1 – Create and Save the Assessment Workflow

Create a new n8n workflow named Topic5_Expressions_Assessment. Add a Manual Trigger
node as the starting point, confirm that the workflow canvas is clean, and save the workflow
before configuring additional nodes.
Expected Output Requirements:
-  Workflow name is exactly Topic5_Expressions_Assessment.
-  Manual Trigger is the first node.
-  The workflow is saved and available in the Workflows dashboard.
Exercise 2 – Generate the Employee Input Data
Add an Edit Fields (Set) node after the Manual Trigger and rename it Generate Employee
Data. Configure three String fields: firstName = john, lastName = smith, and birthDate =
1998-04-12T08:30:00Z. Execute or test the node so its output is available for mapping.
Expected Output Requirements:
-  All three fields are created with the correct names and data type.
-  The input values match the assessment scenario.
-  The node executes successfully and displays valid JSON output.
Exercise 3 – Build the Full Name Expression
Add a second Edit Fields (Set) node and rename it Process Expressions. Create a String field
named fullNameUpperCase. Use a dynamic expression to combine firstName and lastName
with one space and convert the result to uppercase: {{ ($json.firstName + ' ' +
$json.lastName).toUpperCase() }}.
Expected Output Requirements:
-  The value is generated dynamically from incoming fields.
-  The output is JOHN SMITH.
-  No static uppercase full name is hardcoded.
Exercise 4 – Parse and Format the Birth Date
In Process Expressions, create a String field named formattedBirthDate. Parse the incoming
ISO birthDate value and format it as MMMM dd, yyyy using: {{
$dateTime.fromISO($json.birthDate).toFormat('MMMM dd, yyyy') }}.
Expected Output Requirements:
-  The ISO value is referenced from the incoming JSON.
-  The Luxon-based date helper is used correctly.
-  The output is April 12, 1998.

Exercise 5 – Generate the Current Processing Date
Create a String field named processedDate and use the global current-date variable with: {{
$now.toFormat('yyyy-MM-dd') }}. The result must reflect the actual date on which the
learner executes the assessment workflow.
Expected Output Requirements:
-  The date is dynamically generated with $now.
-  The yyyy-MM-dd format is applied correctly.
-  The value is not entered as a fixed date.
Exercise 6 – Execute and Validate the Final Output
Run the complete workflow from the Manual Trigger. Confirm that all nodes display
successful execution indicators and inspect the Process Expressions output in JSON view.
The required transformed fields are fullNameUpperCase, formattedBirthDate, and
processedDate. Retaining the original input fields is acceptable when the Edit Fields node is
configured to include incoming data.
Expected Output Requirements:
-  fullNameUpperCase equals JOHN SMITH.
-  formattedBirthDate equals April 12, 1998.
-  processedDate reflects the execution date in yyyy-MM-dd format.
-  The workflow completes without execution errors.
Exercise 7 – Export, Document, and Prepare Submission Evidence
Export the completed n8n workflow as a JSON file. Create a README that explains the
workflow objective, node sequence, required expressions, setup steps, execution steps,
expected output, and any assumptions. Capture clear screenshots of the workflow canvas,
both Edit Fields configurations, successful execution, JSON output, and execution history.
Expected Output Requirements:
-  Exported workflow JSON is included in the repository.
-  README contains reproducible setup and execution instructions.
-  Screenshots clearly show the required configuration and results.
Expected Final Output
[
{
"fullNameUpperCase": "JOHN SMITH",
"formattedBirthDate": "April 12, 1998",
"processedDate": "<actual execution date in yyyy-MM-dd format>"

}
]
5. Practical Assessment Checklist
Assessment Tracking Item Status
Workflow named
Topic5_Expressions_Assessment created
and saved

[ ]
Manual Trigger configured as the starting
node [ ]
Generate Employee Data node configured
with firstName, lastName, and birthDate [ ]
Employee input values and String data types
verified [ ]
Process Expressions node connected
correctly [ ]
Dynamic string concatenation implemented [ ]
Uppercase conversion implemented with
.toUpperCase() [ ]
ISO birth date parsed using
$dateTime.fromISO() [ ]
Birth date formatted using MMMM dd, yyyy [ ]
Current date generated dynamically using
$now [ ]
Current date formatted using yyyy-MM-dd [ ]
Workflow executed successfully without
errors [ ]
Final JSON output validated [ ]
Workflow JSON exported [ ]
README documentation completed [ ]
Required screenshots captured [ ]
Demo video recorded and accessible [ ]
Public GitHub repository prepared for
submission [ ]
6. Assessment Success Criteria

-  Create and save the required n8n workflow with the correct three-node sequence.
-  Generate the required employee profile input fields using the correct names, values, and
data types.
-  Reference incoming values dynamically using n8n expression syntax instead of
hardcoding transformed outputs.
-  Combine firstName and lastName with a separator and convert the result to uppercase.
-  Parse the ISO birthDate value and format it as a readable date using Luxon-supported
helpers.
-  Generate the current processing date dynamically using $now and the required date
format.
-  Execute the complete workflow successfully and validate the expected output in JSON
view.
-  Export the workflow source, document setup and execution instructions, and submit all
mandatory LMS deliverables.
7. Required Deliverables
Deliverable Required
Loom/YouTube Demo Video Link Mandatory
GitHub Public Repository Mandatory
Exported n8n Workflow JSON and README Mandatory
Configuration, Execution, Output, and
Execution Log Screenshots Mandatory
Description / Additional Comments Recommended
Supporting Documents (PDF/DOCX if
applicable) Optional

8. Submission Guidelines
-  Submit a Loom or YouTube video demonstrating the complete workflow, input data
configuration, all three expressions, successful execution, final JSON output, and
execution history.
-  Submit a public GitHub repository containing the exported n8n workflow JSON file,
README documentation, and required screenshots or an organized evidence folder.
-  Ensure the README explains prerequisites, import/setup steps, node sequence,
expressions used, execution procedure, and expected result.
-  Verify that the repository is publicly accessible and that the workflow JSON can be
imported into n8n.
-  In the LMS Description field, mention challenges faced, resolutions, assumptions,
timezone behavior, known limitations, and any additional improvements implemented.
9. Final Submission Checklist

[ ] Completed all assessment exercises
[ ] Verified all node names, field names, values, and expressions
[ ] Confirmed string concatenation and uppercase transformation
[ ] Confirmed birth-date parsing and formatting
[ ] Confirmed processedDate is dynamically generated
[ ] Executed the workflow successfully and validated final JSON output
[ ] Exported the latest workflow JSON file
[ ] Completed README and supporting evidence
[ ] Pushed the latest files to GitHub
[ ] Verified the GitHub repository is public and accessible
[ ] Uploaded an accessible Loom/YouTube demonstration video
[ ] Added challenges, assumptions, limitations, and comments in the LMS Description field
[ ] Reviewed all deliverables before submission
10. Important Note
Before clicking Submit in the LMS, ensure that you have provided:
1. A Loom or YouTube video link demonstrating the completed n8n Expressions &
Variables workflow and its output.
2. A public GitHub repository containing the exported n8n workflow JSON, README
documentation, and required supporting evidence.
3. Additional comments describing challenges faced, resolutions, assumptions, timezone
considerations, limitations, or extra improvements.
Submissions without the required video demonstration, accessible public GitHub
repository, or importable workflow source may be considered incomplete and may not be
evaluated.
