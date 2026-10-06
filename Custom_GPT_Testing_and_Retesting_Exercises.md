# Custom GPT Testing and Retesting Exercises

## Exercise 1 - Build the Test Checklist

**Task:** Create a checklist of at least 10 test questions covering accuracy, clarity, consistency, and edge cases, including at least one red-teaming case.

### Answer - Setup Steps
- Create test_checklist.md.
- Write 10+ questions spanning all four focus areas.
- Add 1-2 red-teaming questions designed to probe guardrail bypass or hallucination.

## Exercise 2 - Run the Initial Test Pass

**Task:** Run all checklist questions against the GPT and record responses.

### Answer - Setup Steps
- Execute each checklist question.
- Record the GPT's actual response for each.

## Exercise 3 - Identify and Log Failures

**Task:** Compare actual vs. expected behavior and log all failures.

### Answer - Setup Steps
- Review responses against expected behavior.
- Log failures in a ## Failures Identified section with details.

## Exercise 4 - Update Instructions and Retest

**Task:** Revise instructions to address identified failures, then retest and compare results.

### Answer - Setup Steps
- Update the relevant instruction sections (role, scope, tone, format, or guardrails).
- Save as a new version (e.g., instructions_v1.1.md).
- Re-run the full checklist and create before_after_comparison.md.

