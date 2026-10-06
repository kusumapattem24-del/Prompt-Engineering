# Custom GPT Guardrails Exercises

## Exercise 1 - Define Out-of-Scope Guardrails

**Task:** List topics/categories the GPT must never address.

### Answer - Setup Steps
- Create guardrail_rules.md.
- List out-of-scope topics based on the GPT's defined scope.

## Exercise 2 - Define Sensitive Information Guardrails

**Task:** List categories of sensitive data the GPT must never disclose.

### Answer - Setup Steps
- List sensitive data categories (e.g., personal employee data, confidential financials).
- Add rules preventing disclosure even under direct request.

## Exercise 3 - Write Fallback/Refusal Responses

**Task:** Draft 3 polite, clear refusal response templates.

### Answer - Setup Steps
- Draft refusal templates covering out-of-scope, sensitive, and ambiguous scenarios.
- Save under ## Sample Refusal Responses.

## Exercise 4 - Integrate and Test Guardrails

**Task:** Add guardrails to instructions and test against prohibited and ambiguous questions.

### Answer - Setup Steps
- Insert guardrail rules and refusal templates into the instruction block under ## Guardrails.
- Test 2 prohibited questions and 1-2 ambiguous/borderline questions.
- Record results and confirm refusals are polite, clear, and consistent.

