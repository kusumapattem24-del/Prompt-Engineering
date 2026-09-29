# AI Research & Knowledge Assistant - Assessment Tasks & Answers

Create a folder on your computer named `prompt-engineering-researcher`
to organize your deliverables.

## Exercise 1 - Set Up the Research Workspace and Generate Background Knowledge

**Task:** Open a fresh ChatGPT session, identify the three container
orchestration technologies to be studied, and execute the Generated
Knowledge Prompt to compile a verified background fact sheet before
drafting any report.

### Answer - Setup Steps

-   Open your browser and navigate to `https://chatgpt.com/` and log in
    to your account.
-   Click the **New Chat** button to clear any prior conversation
    context and start a clean research session.
-   Confirm the three technologies that will be compared throughout this
    project: **Kubernetes (K8s), Docker Swarm, and AWS Fargate
    (Serverless Containers)**.
-   In your text editor, draft the Generated Knowledge Prompt as
    follows:

``` text
Generate a factual summary detailing the core architecture, scalability limits,
setup complexity, and cost structures of the following three technologies:
Kubernetes, Docker Swarm, and AWS Fargate. Focus on raw specifications, documentation
facts, and industry statistics. Do not write a comparison or recommendations yet.
Keep your focus on compiling background knowledge.
```

-   Paste the prompt into ChatGPT and run it.
-   Review the output to verify key factual points - such as Kubernetes
    node limits, Docker Swarm's built-in status, and AWS Fargate's
    pay-as-you-go pricing - are present and accurate.
-   Save this compilation locally as your background fact sheet. This
    fulfills **REQ-001 (Knowledge Grounding)**.

## Exercise 2 - Draft the Baseline Research Report Using the ERA Framework

**Task:** Use the ERA (Expectation, Role, Action) framework to write and
execute a structured research prompt in ChatGPT that produces an
initial, unverified comparison report based on the fact sheet generated
in Exercise 1.

### Answer - Setup Steps

-   In your text editor, draft the ERA Research Prompt using the three
    ERA parameters as follows:

``` text
[EXPECTATION]: I expect a detailed comparison report comparing Kubernetes, Docker
Swarm, and AWS Fargate. Structure the response with H2 headers for: Introduction,
Tech Overviews, Detailed Comparison, and Final Verdict. Do not write summary tables yet.

[ROLE]: Act as a Lead Systems Architect.

[ACTION]: Write the comparison report based on the following background facts:

=== BACKGROUND FACTS ===
[Insert the fact sheet generated in Exercise 1]
```

-   Run the prompt in ChatGPT.
-   Copy the full output text and save it in a local scratch file
    labeled `baseline_draft.txt`. This baseline draft will be used as
    the input for the CoVe audit cycle in the next exercise. This
    fulfills **REQ-002 (ERA Prompting)**.

## Exercise 3 - Execute the Full Chain of Verification (CoVe) Cycle

**Task:** Audit the baseline draft using a 4-step self-correcting
verification loop - formulating verification questions, independently
answering them with verified facts, and producing a corrected final
report.

### Answer - Setup Steps

-   Draft the CoVe Question Formulation Prompt:

``` text
Read the baseline draft comparison below. Formulate a list of exactly four specific
verification questions that can be answered with absolute facts to audit the claims,
numbers, and limitations stated in the text (e.g. check version limits, specific
scalability numbers, or operational dependencies).

[BASELINE DRAFT]:
[Insert the text from baseline_draft.txt]
```

-   Run the prompt. ChatGPT will output four targeted audit questions
    (e.g., `"Does Docker Swarm require external key-value stores?"`,
    `"What is the node limit of Kubernetes?"`).
-   Draft the CoVe Question Answering Prompt:

``` text
Answer each of the following verification questions one-by-one. Rely strictly on
verified developer documentation facts:

[Insert the four questions generated in the previous step]
```

-   Run the prompt and capture the verified answers.
-   Draft the CoVe Correction Prompt:

``` text
Review the original baseline draft. Rewrite the report incorporating the verified
corrections below. Ensure the final report is fully accurate and resolved.

[BASELINE DRAFT]: [Insert baseline_draft.txt]

[VERIFIED CORRECTIONS]: [Insert the answers from the previous step]
```

-   Execute the prompt in ChatGPT. Copy the corrected final output. This
    will form the core of your Research Report. This fulfills **REQ-003
    (Fact Verification / CoVe Audit Trail - TR-002)**.

## Exercise 4 - Run the Assumption Audit and Compile the Comparison Matrix & Executive Summary

**Task:** Audit the finalized research report for hidden latent biases
using the Assumption Audit Prompt, then generate the Comparison Matrix
and a 150-word Executive Summary.

### Answer - Setup Steps

-   Draft the Assumption Audit Prompt:

``` text
Analyze the finalized technology comparison below. Identify and list 3 hidden
assumptions the writer makes regarding the technologies (e.g. assuming high capital
expense always correlates with higher quality, or assuming simplicity is always
better for small teams). Detail if these assumptions introduce bias.

[FINALIZED REPORT]:
[Insert the corrected report from Exercise 3]
```

-   Execute the prompt in ChatGPT. Save the assumption list. This
    fulfills **REQ-004 (Bias Identification)**.
-   Draft the Comparison Matrix Prompt:

``` text
Create a markdown table comparing Kubernetes, Docker Swarm, and AWS Fargate across
these columns: Technology, Scalability (High/Med/Low), Setup Complexity
(High/Med/Low), Operational Overhead (High/Med/Low), Cost Model (e.g. Pay-per-node,
Pay-per-use, Free).
```

-   Run the prompt and save the output as `comparison_matrix.md`. This
    fulfills **REQ-005 and TR-003**.
-   Draft the Executive Summary Prompt:

``` text
Write a 150-word executive summary synthesizing the comparison findings. Recommend
the best technology for a fast-growing startup prioritizing speed over infrastructure
scaling.
```

-   Run the prompt and save the output as `executive_summary.md`.

## Exercise 5 - Record the Loom Video and Push All Deliverables to GitHub

**Task:** Record a 3-to-4 minute Loom video demonstrating your research
architecture and live CoVe process, then organize and push all
deliverables to a public GitHub repository.

### Answer - Setup Steps

-   Sign in to Loom at `https://www.loom.com/` and configure your
    screen-share and webcam bubble.
-   Follow this structured timeline for your recording:
    -   **0:00 - 0:45:** State the project name (**AI Research &
        Knowledge Assistant**) and explain the CoVe methodology and why
        it prevents hallucinations.
    -   **0:45 - 2:00:** Show your `prompt_documentation.md` file.
        Explain the ERA parameters and walk through all 4 CoVe steps.
    -   **2:00 - 3:15:** Open your browser tab with ChatGPT. Paste your
        CoVe Question Answering Prompt live and run it. Show how ChatGPT
        checks its own draft.
    -   **3:15 - 3:45:** Show the final Comparison Matrix table and
        close the video.
-   Copy the public Loom share URL. This fulfills **REQ-007**.
-   Create a local folder named `prompt-engineering-researcher` and move
    the following files into it:
    -   `research_report.md` - Contains background fact sheet, final
        verified text, and the 4 CoVe steps log.
    -   `executive_summary.md` - The 150-word summary.
    -   `comparison_matrix.md` - The scored Markdown table.
    -   `prompt_documentation.md` - Contains the exact ERA and CoVe
        prompt templates with parameters.
    -   `README.md` - Contains project title, objectives, your name, and
        the Loom video URL.
-   Open a terminal inside the folder and run the following Git
    commands:

``` bash
git init
git add .
git commit -m "Initialize Prompt Engineering Research Assistant project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/prompt-engineering-researcher.git
git push -u origin main
```

-   Confirm your repository is set to public and is viewable from an
    incognito browser tab. This fulfills **REQ-006 (GitHub Submission -
    TR-001)**.
