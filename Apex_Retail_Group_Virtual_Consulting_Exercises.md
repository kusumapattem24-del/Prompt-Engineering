# Apex Retail Group --- Virtual Consulting Hands-On Exercises

## Exercise 1 --- Set Up the Virtual Consulting Workspace & Case Study

**Task:** Initialize your consulting environment in ChatGPT by setting
up the Apex Retail Group B2B client dossier as your working context.
Familiarize yourself with the key client metrics that will drive all
subsequent prompts.

### Answer --- Setup Steps

-   Open your browser and navigate to `https://chatgpt.com/` and log in
    to your account.
-   Click the **New Chat** button to open a clean thread free of prior
    context.
-   Open a local text editor and create your draft workspace by copying
    and pasting the following B2B retail client matrix:

``` text
=== CLIENT DOSSIER: APEX RETAIL GROUP ===
- Background: Apex operates 45 brick-and-mortar apparel stores.
- Financials: Annual revenue is $12M, but margins have declined by 15% due to inventory carry costs.
- Foot Traffic: Decreased by 25% year-over-year.
- E-commerce: Active online store, but cart abandonment is at 82% and conversion rate is low (1.2%).
- Operational Bottlenecks: Over-stocked warehouses, slow shipping speeds (5-7 days), manual inventory tracking.
=========================================
```

-   Review and familiarize yourself with all client metrics as they will
    be referenced in every subsequent prompt stage.
-   Confirm the workspace is ready before proceeding to the diagnostic
    prompting stage.

## Exercise 2 --- Run the 'Assess' & 'Pinpoint' Stages (CoT Diagnosis)

**Task:** Apply Chain of Thought (CoT) and Persona prompting to analyze
the Apex Retail Group's current state, perform a SWOT analysis, identify
the single most critical root-cause bottleneck, and generate a gap
analysis comparing their current state with an optimized state
(REQ-001).

### Answer --- Setup Steps

-   In your text editor, draft the APEX Diagnostic Prompt:

``` text
Act as a Senior Management Consultant. We need to perform the ASSESS and PINPOINT stages for our B2B retail client, Apex Retail Group.

[CLIENT METRICS]:
- 45 physical stores.
- Annual revenue: $12M. Margins down 15% due to inventory carry costs.
- Foot traffic down 25%.
- E-commerce conversion rate: 1.2%. Cart abandonment: 82%.
- Bottlenecks: Over-stocked warehouses, 5-7 days shipping, manual inventory tracking.

Let's think step-by-step to diagnose the situation:
1. Conduct a SWOT analysis based on the metrics.
2. Pinpoint the single most critical root-cause bottleneck. Explain your logic.
3. Generate a gap analysis comparing their current state with an optimized state.
```

-   Paste the prompt into ChatGPT and run it.
-   Review the output. Verify that the model highlights how inventory
    carry costs and manual tracking are draining margins. Copy the
    diagnostics output to your local scratch file.

## Exercise 3 --- Run the 'Evaluate' Stage (Tree of Thoughts)

**Task:** Use Tree of Thoughts (ToT) prompting to generate and evaluate
three distinct competitive strategic solution branches for Apex Retail
Group, scoring each out of 10 and selecting the best candidate
(REQ-002).

### Answer --- Setup Steps

-   Draft the ToT Evaluation Prompt:

``` text
We need to evaluate strategic solutions for Apex Retail Group. Generate three distinct solution branches:

- Branch A: E-Commerce & Logistics Overhaul (Optimize online checkout, integrate automated inventory, and switch to 3PL shipping).
- Branch B: Retail Footprint Downsizing (Close the 15 lowest-performing stores, consolidate inventory, and reinvest capital).
- Branch C: Hybrid B2B Licensing (Franchise physical stores, license the brand, and pivot corporate focus to online wholesale).

Evaluate each branch in parallel. For each option, analyze:
1. Estimated Impact on Margins (High/Med/Low).
2. Capital Expenditure (CapEx) required (High/Med/Low).
3. Execution Risk.

Let's think step-by-step. Score each branch out of 10 and select the best candidate.
```

-   Run the prompt in ChatGPT. Copy the output candidate paths to your
    local scratch file.
-   **Self-Consistency Check:** Open a new ChatGPT thread, paste the
    same prompt, and verify if it selects the same winning branch
    (usually Branch A or a combination of A & B).

## Exercise 4 --- Build the Weighted Decision Matrix

**Task:** Create a mathematically sound weighted decision matrix in
Markdown format comparing all three strategic branches using criteria
with weights that sum to 100% (REQ-003, TR-002).

### Answer --- Setup Steps

-   Draft the Decision Matrix Prompt:

``` text
Act as an Analyst. Create a markdown table comparing Branch A, Branch B, and Branch C.

Use these criteria and weights (weights must sum to 100%):
- ROI (30% weight)
- Low Execution Risk (20% weight)
- Implementation Speed (20% weight)
- Resource Alignment (30% weight)

For each option, assign a score from 1 (poor) to 10 (excellent) for each criterion,
calculate the weighted score, and sum them to find the winner.

Format:
| Solution | Criterion | Weight | Score (1-10) | Weighted Score |
```

-   Verify the calculations manually:
    `Weighted Score = Raw Score × Weight` (e.g. if ROI is scored 9, the
    weighted score is `9 × 0.30 = 2.70`).
-   Ensure the column weights sum to exactly 100% (or 1.0) as required
    by US-003.
-   Copy the Markdown table to your `decision_matrix.md` draft file.

## Exercise 5 --- Run the 'Execute' Stage (Roadmapping & Risks)

**Task:** Generate a phased 12-month implementation roadmap and a risk
mitigation registry for Branch A (E-Commerce & Logistics Overhaul) using
Planning Prompting (REQ-004, TR-003).

### Answer --- Setup Steps

-   Draft the Roadmap Planning Prompt:

``` text
We have selected Branch A (E-Commerce & Logistics Overhaul) as the winner. Act as a Project Manager.

First, outline the three distinct implementation phases over a 12-month timeline. Pause and write only the phase names and durations.

Once I say "Execute", write the detailed milestones, activities, and RACI assignments for each phase.
```

-   Send the prompt. Once ChatGPT outputs the phase outline, type
    `Execute`.
-   Draft the Risk Log Prompt:

``` text
For the selected overhaul strategy, identify 3 critical implementation risks.

Format your response as a markdown table with columns:
- Risk Event
- Probability (Low/Med/High)
- Impact (Low/Med/High)
- Mitigation Strategy
```

-   Copy the generated roadmap and risk log outputs to your
    `implementation_roadmap.md` draft file.
