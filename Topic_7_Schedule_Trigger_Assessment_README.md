# Topic 7 Assessment — Schedule Trigger Automation

**Course:** n8n Hands-On Beginner Course  
**Workflow name:** `Topic7_Schedule_Trigger_Assessment`  
**Workflow:** `Schedule Trigger → Log Execution (Edit Fields / Set)`

## Assessment Overview

Configure, test, activate, and document an n8n Schedule Trigger workflow with two schedules and a dynamic execution timestamp.

## Objective

Run daily at 09:00 and on weekdays at 08:30 using cron 30 8 * * 1-5. Log the execution time using $now and submit reproducible evidence.

## Prerequisites

Review the Requirement Document and Implementation Plan; complete Topics 1-6; obtain n8n workflow editing/activation permissions and a GitHub account.

## Exercise 1 - Create and Name the Workflow

Create a new workflow named Topic7_Schedule_Trigger_Assessment. Add Schedule Trigger as the first node; do not add a Manual Trigger. Save.

## Exercise 2 - Daily Schedule

Within Schedule Trigger, configure a schedule rule: Trigger Interval = Days, interval = 1, time = 09:00 (9:00 AM).

## Exercise 3 - Weekday Cron

Add a second schedule rule to the same Schedule Trigger. Select Custom/Cron Expression and enter 30 8 * * 1-5. This runs Monday through Friday at 08:30 in the configured workflow timezone.

## Exercise 4 - Log Execution

Connect Schedule Trigger to an Edit Fields (Set) node named Log Execution. In Manual Mapping, add a String field executionTime. Set its value to the expression {{ $now.toFormat('yyyy-MM-dd HH:mm:ss') }}. Disable Include Other Input Fields if only executionTime should appear.

## Exercise 5 - Activate and Submit

Test the workflow and inspect Log Execution output in JSON view. Save and activate/publish the workflow as supported by your n8n version. Verify an actual scheduled run when it occurs; export the workflow JSON, capture screenshots, record a Loom/YouTube demonstration, and push files to a public GitHub repository.

## Cron Syntax

30 = minute; 8 = hour; * = every day of month; * = every month; 1-5 = Monday-Friday. If your n8n cron field requires seconds, use 0 30 8 * * 1-5 instead, while documenting the assessment-required five-field form.

## Validation and Evidence

Verify two rules in one trigger, the correct 09:00 and 08:30 times, green node execution, dynamic executionTime, saved/active status, and execution history. Manual test evidence does not by itself prove a scheduled run occurred.

## Required Deliverables

Mandatory: Loom/YouTube video link; public GitHub repository; exported n8n workflow JSON and README; workflow and execution screenshots. Recommended: LMS Description with challenges, resolutions, timezone assumptions, limitations and evidence.

## Submission Checklist

[ ] Exact workflow name; [ ] Schedule Trigger first; [ ] daily 09:00; [ ] cron 30 8 * * 1-5; [ ] Log Execution with dynamic timestamp; [ ] successful test; [ ] saved and activated; [ ] exported JSON; [ ] screenshots; [ ] public GitHub; [ ] video; [ ] LMS comments.

## Important Notes

Schedule times follow the n8n workflow/instance timezone. The sample timestamp is illustrative, not evidence of a run. Do not substitute a temporary testing cron expression for the required weekday cron in the final submission. No actual n8n execution, GitHub upload, or video recording is claimed in this document.

## Configuration Reference

| Component | Setting | Value |
|---|---|---|
| Schedule Trigger | Rule 1 | Days, interval 1, 09:00 |
| Schedule Trigger | Rule 2 | Custom cron: `30 8 * * 1-5` |
| Log Execution | Field name / type | `executionTime` / String |
| Log Execution | Expression | `{{ $now.toFormat('yyyy-MM-dd HH:mm:ss') }}` |

## Expected JSON Output

```json
[
  {
    "executionTime": "<actual execution timestamp in yyyy-MM-dd HH:mm:ss format>"
  }
]
```

## Suggested GitHub Structure

```text
Topic7_Schedule_Trigger_Assessment/
├── README.md
├── Topic7_Schedule_Trigger_Assessment.json  # export from n8n
└── screenshots/
    ├── workflow-canvas.png
    ├── daily-schedule.png
    ├── weekday-cron.png
    ├── log-execution.png
    ├── successful-output.png
    └── execution-history.png
```

## LMS Submission Template

- **Video:** [add actual Loom/YouTube URL]
- **GitHub:** [add actual public repository URL]
- **Comments:** [describe challenges, resolutions, timezone, limitations, and verification evidence]
