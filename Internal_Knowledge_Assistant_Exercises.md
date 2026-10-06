# Internal Knowledge Assistant Exercises

## Exercise 1 - Gather Knowledge Files

**Task:** Collect at least one policy document and one FAQ/process guide, cleaned and sectioned.

### Answer - Setup Steps
- Gather and clean the two required document types.
- Ensure clear headings and no conflicting content across files.

## Exercise 2 - Build the Instruction Block

**Task:** Write instructions defining the GPT as an internal knowledge assistant that answers only from uploaded documents.

### Answer - Setup Steps
- Define Role: Internal Company Knowledge Assistant.
- Define Scope: answer only from uploaded documents; refuse unknown/out-of-scope topics.
- Save as instruction_block.md.

## Exercise 3 - Add Behavior Rules and Guardrails

**Task:** Add rules preventing hallucination, opinions, and speculative answers, and requiring source referencing.

### Answer - Setup Steps
- Add: no personal opinions, no external knowledge, no speculative answers.
- Add: must reference document sections where applicable.

## Exercise 4 - Test the Three Coverage Scenarios

**Task:** Test a fully covered, partially covered, and uncovered question.

### Answer - Setup Steps
- Run all three test scenarios.
- Record results in test_results.md.

