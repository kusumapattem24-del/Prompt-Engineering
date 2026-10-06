# ERP Functional Support Assistant Exercises

## Exercise 1 - Gather ERP Documentation

**Task:** Collect ERP process documents, SOPs, transaction manuals, and error-resolution guides.

### Answer - Setup Steps
- Gather and upload all four document types relevant to the target ERP system.

## Exercise 2 - Build the Instruction Block

**Task:** Write instructions defining the GPT as an ERP Functional Support Assistant with a Purpose -> Steps -> Common Issues response structure.

### Answer - Setup Steps
- Define Role: ERP Functional Support Assistant.
- Define output structure and core capabilities (process explanation, transaction guidance, concept clarification).
- Save as instruction_block.md.

## Exercise 3 - Add Guidance-Only Guardrails and Flow

**Task:** Add rules preventing live data access/transaction execution, and define the module/role identification flow.

### Answer - Setup Steps
- Add: must not access live ERP data, execute transactions, or change configurations.
- Add: must state it is guidance-only; must escalate system-access issues.
- Define flow: Identify module -> Understand role -> Provide guided explanation -> Suggest next steps/escalation.

## Exercise 4 - Test Module/Role Scenarios

**Task:** Test a clear in-scope process question, missing module/role context, a transaction-execution request, and an uncovered question.

### Answer - Setup Steps
- Run all four test scenarios.
- Record results in test_results.md.

