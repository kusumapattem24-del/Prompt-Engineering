# Custom GPT Instructions and Testing Exercises

## Exercise 1 - Draft Role, Scope, Tone, and Output Format

**Task:** Write clear definitions for Role, Scope, Tone, and Output Format based on your Topic 1 use case.

### Answer - Setup Steps
- Create `instruction_block.md`.
- Draft each of the four components as its own bulleted section.
- Ensure Scope explicitly states what the GPT can and cannot do.

## Exercise 2 - Add Constraints

**Task:** Add at least 3 explicit constraints, including refusal and error-handling behavior.

### Answer - Setup Steps
- Add a `## Constraints` section with 3+ rules (for example, never fabricate information and never answer out-of-scope questions).
- Include one rule for handling missing or unclear input.

## Exercise 3 - Load Instructions and Configure the GPT

**Task:** Assemble the full instruction block and load it into a Custom GPT builder.

### Answer - Setup Steps
- Combine Role, Scope, Tone, Output Format, and Constraints into a single instruction block.
- Paste the complete instruction block into the GPT builder's system instructions field and save the configuration.

## Exercise 4 - Test and Document Consistency

**Task:** Run 5 varied test queries - in-scope, out-of-scope, casual, vague, and format-specific - and document the results.

### Answer - Setup Steps
- Run each query and record the GPT's response.
- Create `test_results_summary.md` and log: Query, Expected Behavior, Observed Behavior, and Consistent (Yes/No).
- Note any instruction component that needs refinement.
