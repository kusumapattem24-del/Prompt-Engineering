# Data Analysis Assistant Exercises

## Exercise 1 - Enable Code Interpreter

**Task:** Enable Code Interpreter (or equivalent) in the GPT builder.

### Answer - Setup Steps
- Enable the tool under Capabilities in the GPT configuration.

## Exercise 2 - Build the Instruction Block

**Task:** Write instructions defining the GPT as a Data Analysis Assistant for non-technical users.

### Answer - Setup Steps
- Define Role: Data Analysis Assistant for business users/non-technical stakeholders.
- Define behavior: explain findings in plain language, avoid jargon unless requested.
- Save as instruction_block.md.

## Exercise 3 - Add Tool Governance and Anti-Fabrication Guardrails

**Task:** Add rules for when to use the tool and prevent fabricated insights.

### Answer - Setup Steps
- Add: use tool only when necessary; explain what is being analyzed and why.
- Add: no assumptions without data; ask clarifying questions if dataset/goal is unclear; never fabricate insights.

## Exercise 4 - Test Across Data Scenarios

**Task:** Test a dataset with a clear objective, one without, incomplete/incorrect data, and a request needing clarification.

### Answer - Setup Steps
- Upload the sample dataset and run all four test scenarios.
- Record results in test_results.md.

