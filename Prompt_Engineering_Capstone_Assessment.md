# Prompt Engineering Capstone --- Assessment Tasks & Answers

## Exercise 1 --- Select the Enterprise Case Study Scenario

**Task:** Establish your enterprise parameters in ChatGPT by defining
the Apex Cloud Services CRM migration scenario, including user count,
current state, and vendor financial metrics for Salesforce, HubSpot, and
Zoho.

### Answer --- Setup Steps

-   Open your browser and navigate to `https://chatgpt.com/`. Log in and
    click **New Chat** to clear the conversation window.
-   Define the scenario: Apex Cloud Services is migrating **150 active
    sales representatives**, currently tracking client data in offline
    spreadsheets with high data fragmentation (REQ-002).
-   Record the financial metrics for each vendor:
    -   Salesforce: **\$150/user/month + \$25,000 setup**
    -   HubSpot: **\$90/user/month + \$10,000 setup**
    -   Zoho: **\$40/user/month + \$5,000 setup**
-   Confirm this baseline context is established in the chat thread
    before running any evaluation prompts.

## Exercise 2 --- Run Meta-Prompting and the CO-STAR Q-GoT Vendor Evaluation

**Task:** Draft a Meta-Prompt instructing ChatGPT to generate a
specialized B2B CRM research prompt, then execute a CO-STAR-structured
prompt combined with Q-GoT calculations to determine 1-year and 3-year
Total Cost of Ownership (TCO) for each vendor.

### Answer --- Setup Steps

-   **Meta-Prompt:** Act as an expert Prompt Engineer. Write a system
    prompt turning ChatGPT into a specialized B2B CRM Pricing and
    Feature Researcher, focused on comparing Salesforce Enterprise,
    HubSpot Sales Hub, and Zoho CRM, enforcing verified licensing models
    and structured Markdown output (REQ-003).
-   Save the generated prompt block into `prompt_portfolio.md`.
-   **CO-STAR Q-GoT Prompt:** Use:
    -   **Context:** Apex Cloud Services, 150 reps, and the three vendor
        cost structures.
    -   **Objective:** Run a Q-GoT evaluation to calculate 1-year and
        3-year TCO.
    -   **System Controls:** Calculate
        `TCO = User Count × Cost/month × Months + Setup Fee`, then
        self-check the arithmetic.
    -   **Style:** McKinsey Strategy Consultant.
    -   **Tone:** Objective, analytical, finance-first.
    -   **Audience:** CEO and Board of Directors.
    -   **Response:** Structured Markdown analysis with a recommendation
        (REQ-001, CON-001).
-   Execute the prompt and save the verified TCO output.

## Exercise 3 --- Build the Weighted Decision Matrix and Phased Roadmap

**Task:** Generate a Markdown decision matrix scoring the three vendors
against weighted criteria, then produce a 6-month Gantt roadmap and risk
registry for the selected vendor.

### Answer --- Setup Steps

-   Create the Decision Matrix prompt using four criteria:
    -   TCO Cost Model --- **30%**
    -   Customization & Scale --- **20%**
    -   Setup Speed --- **25%**
    -   User Adoption Ease --- **25%**
-   Use raw scores from 1--10 multiplied by the weight (TR-002).
-   Verify the weights sum to exactly **1.0 (100%)** and confirm the
    math steps shown, for example:
    `Weighted Score = Raw Score × Weight`.
-   Save the matrix to `decision_matrix.md`.
-   Generate the Roadmap & Gantt prompt for the selected vendor
    (**HubSpot**), covering:
    -   Phase 1 --- Planning & Data Cleanup (Month 1)
    -   Phase 2 --- System Configuration & Pilot (Months 2--3)
    -   Phase 3 --- Full Migration & Staff Training (Months 4--5)
    -   Phase 4 --- Post-Launch Optimization (Month 6)
-   Format the roadmap as a Markdown text Gantt chart (REQ-004).
-   Generate the Risk Registry prompt identifying 3 implementation risks
    in a table with **Risk Event, Probability, Impact, and Mitigation**
    columns.
-   Save both to `implementation_plan.md`.

## Exercise 4 --- Write the Business Proposal, Executive Presentation, and Lessons Learned Report

**Task:** Compile a B2B business proposal and a 6-slide executive
presentation using Markdown slide dividers, then write a lessons learned
report reflecting on LLM capabilities and limitations.

### Answer --- Setup Steps

-   Generate the Executive Presentation prompt producing 6 slides:
    1.  Title & Overview
    2.  Client Problem & Metrics
    3.  Vendor Candidates
    4.  Cost-Benefit Analysis & TCO
    5.  Decision Matrix & Recommendation
    6.  Phased Roadmap & Next Steps
-   Separate the slides using exactly three dashes (`---`) (REQ-005,
    TR-003).
-   Save the slide deck to `executive_presentation.md` and the full
    proposal text to `business_proposal.md`.
-   Create `lessons_learned_report.md` covering:
    -   **Hallucination Prevention:** How step-by-step math audits
        prevented calculation errors.
    -   **Context Window Wind-down:** How model performance degrades
        over long threads and how to manage it.
    -   **Framework Alignment:** When to use RGCCO, CARE, ERA, or
        CO-STAR (REQ-006, CON-002).

## Exercise 5 --- Record Loom, Organize, and Push Deliverables to GitHub

**Task:** Record a 4-to-6-minute Loom video demonstrating the capstone
system, then organize all files into a local project folder and push
them to a public GitHub repository.

### Answer --- Setup Steps

-   Log in to Loom, set up screen and webcam bubble, and record a paced
    4--6 minute walkthrough:
    -   **0:00--1:00:** Introduce yourself and summarize the B2B CRM
        migration case study.
    -   **1:00--2:00:** Walk through your `prompt_portfolio.md` library
        and explain CO-STAR and Q-GoT techniques.
    -   **2:00--4:00:** Paste the CO-STAR Q-GoT vendor evaluation prompt
        live in ChatGPT and show the 1-year and 3-year TCO calculated
        step-by-step.
    -   **4:00--5:30:** Show `executive_presentation.md` slide
        formatting and explain the `lessons_learned_report.md` insights.
-   Copy the public Loom share URL, ensuring sharing is set to **"Anyone
    with the link can view."**
-   Create a local folder named `prompt-engineering-capstone` and move
    in:
    -   `prompt_portfolio.md`
    -   `decision_matrix.md`
    -   `business_proposal.md`
    -   `implementation_plan.md`
    -   `executive_presentation.md`
    -   `lessons_learned_report.md`
    -   `README.md` --- with title, objectives, your name, and the Loom
        URL (REQ-007, TR-001).
-   Open a terminal inside the folder and run:

``` bash
git init
git add .
git commit -m "Initialize Prompt Engineering Capstone project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/prompt-engineering-capstone.git
git push -u origin main
```

-   Confirm the repository is public and viewable from an incognito
    browser tab.
