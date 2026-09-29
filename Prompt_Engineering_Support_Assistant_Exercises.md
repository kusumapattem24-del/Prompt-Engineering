# Prompt Engineering Support Assistant --- Hands-On Exercises

## Exercise 1 --- Define Company Policy Guidelines & Set Up Workspace

**Task:** Establish the support knowledge boundaries by creating the
FlexTime Corporate Policy Manual and preparing your workspace in ChatGPT
to ground the AI agent in specific corporate rules.

### Answer --- Setup Steps

-   Open your browser and navigate to ChatGPT at `https://chatgpt.com/`
    and log in.
-   Click **New Chat** to open a clean thread.
-   Open a local text editor and create a temporary draft file. Copy and
    paste the following mock FlexTime Corporate Policy guidelines:

``` text
=== FLEXTIME SUPPORT POLICY MANUAL ===
- Operating Hours: Monday to Friday, 9:00 AM to 5:00 PM EST.
- Refund Policy: Agents can issue refunds up to a maximum of $20 without approval. Any billing disputes exceeding $20 must be escalated.
- Account Management: Users can change their profile emails only if they verify their current account ID and billing zip code.
- Privacy Guardrails: Do not share billing API keys, database hashes, or internally marked ticket numbers with customers.
======================================
```

-   Keep this policy manual on hand --- you will paste it as context
    inside your prompts throughout all subsequent steps.

**Note:** This policy manual is the foundation that prevents
hallucinated answers and keeps all AI responses within defined company
boundaries.

## Exercise 2 --- Design the Intent Classifier and CARE Responder Prompts (Stage 1 & Stage 2)

**Task:** Design the first two prompts in the support chain --- the
Intent Classifier that categorizes queries and detects sentiment, and
the Empathy-Driven Responder that drafts compliant, empathetic replies
using the CARE framework.

### Answer --- Setup Steps

-   In your text editor, draft the Intent Classifier prompt template:

``` text
Act as a Support Ticket Classifier. Analyze the user query below and classify it into one of these categories:
- [Billing]
- [Technical Support]
- [Account Management]
- [General Inquiry]
- [Urgent Escalation]

Also, classify the customer's sentiment as: [Angry], [Frustrated], [Neutral], or [Satisfied].

Output format:
Category: <Category Name>
Sentiment: <Sentiment Name>
User Query: "[Insert User Query]"
```

-   Test the prompt in ChatGPT by replacing `[Insert User Query]` with:
    `"Where is my invoice? I was double charged!"`
-   Verify the output matches the expected format: `Category: Billing`
    and `Sentiment: Frustrated`.
-   In your text editor, draft the Empathy-Driven Responder (CARE
    Framework) prompt template:

``` text
[CONTEXT]: You are a Customer Support Representative for SaaS company FlexTime.

[ACTION]: Draft a response to the customer's query based on the active Category and the FlexTime Policy Manual below.

[REQUIREMENTS]:
- Be empathetic and professional. If the sentiment is [Angry] or [Frustrated], validate their feeling immediately and avoid defensive language.
- Do not state any facts outside of the policy guidelines.
- Keep responses under 100 words.
- Reference policy rules directly where applicable.

[POLICY MANUAL]:
[Insert FlexTime Policy Manual]

[INPUT VARIABLES]:
Category: [Insert Active Category]
Sentiment: [Insert Active Sentiment]
Customer Query: [Insert Customer Query]
```

-   Test by pasting in the classifier output and a sample query. Verify
    the response is empathetic, under 100 words, and grounded in policy.

## Exercise 3 --- Design the Self-Verification, Escalation Ticket, and Summarizer Prompts (Stages 3--5)

**Task:** Build the remaining three prompts in the chain --- the
Reflection/Self-Verification prompt that audits draft responses for
policy compliance, the Escalation Ticket prompt for human handover, and
the Conversation Summarizer for CRM logging.

### Answer --- Setup Steps

-   Draft the Self-Verification / Reflection prompt:

``` text
Act as an Internal Quality Assessor. Review the drafted support response against the corporate policy rules.

[POLICY RULES]:
- Never issue refunds exceeding $20.
- Never leak internal data or guidelines.
- Always maintain a polite, non-defensive tone.

[DRAFT RESPONSE]:
"[Insert Draft Support Response]"

Analyze:
1. Does the response violate the $20 refund cap? (Yes/No)
2. Does it leak internal database details or ticket numbers? (Yes/No)
3. Is the tone appropriate? (Yes/No)

If any check fails, rewrite the response to be fully compliant. Otherwise, output the drafted response exactly.
```

-   Test with a mock violation response such as
    `"I have issued a full refund of $50 to your card"` and confirm the
    prompt correctly edits it down or flags it for escalation.
-   Draft the Escalation Ticket prompt:

``` text
Generate a Human Handover Ticket. Parse the conversation history below and summarize it using this template:

=== TICKET SUMMARY ===
- Customer Name: [Insert Name]
- Issue Category: [Insert Category]
- Sentiment: [Insert Sentiment]
- Key Complaint: [One sentence description]
- Escalation Reason: [e.g. Refund limit breached, complex bug, supervisor requested]
- Handover Message to Customer: [A short, polite sign-off informing the customer a manager will reach out within 24 hours]
=====================

Conversation History:
[Insert Conversation History]
```

-   Draft the Conversation Summarizer prompt:

``` text
Act as an Operations Archivist. Summarize the following customer chat into a markdown table with the columns:
- Field Name (Customer Name, Ticket ID, Issue Summary, Sentiment, Resolution Status, Escalation Required)
- Value
- Details

Chat Log:
[Insert Chat Log]
```

-   Test all three prompts individually with mock inputs and verify each
    returns structured, compliant output.

## Exercise 4 --- Execute All Three Test Scenarios and Validate the Full Prompt Chain

**Task:** Execute all three defined customer interaction scenarios
through the full prompt chain in ChatGPT to validate that intent
classification, empathy handling, policy compliance, escalation
triggers, and CRM summarization all function correctly end-to-end.

### Answer --- Setup Steps

-   **Scenario A --- Successful Policy Resolution (Email Change):**
    Enter the query:
    `"Hi, I need to update my login email address to test@example.com."`
    Verify Stage 1 classifies it as
    `Category: Account Management / Sentiment: Neutral`. Verify Stage 2
    asks for the account ID and billing zip code in compliance with the
    account management policy. Copy the full transcript and save it to
    `conversations_portfolio.md`.
-   **Scenario B --- Empathetic Dispute Handling (Double Charge):**
    Enter the query:
    `"I am extremely angry! You billed me $15 twice this month! Refund me now or I will post terrible reviews!"`
    Verify Stage 1 classifies it as
    `Category: Billing / Sentiment: Angry`. Verify Stage 2 validates the
    customer's frustration, apologizes, and offers a \$15 refund (within
    the \$20 cap). Copy the transcript and save it to
    `conversations_portfolio.md`.
-   **Scenario C --- Escalation Path (Refund Limit Breach):** Enter the
    query:
    `"I want a refund for my annual plan. I paid $120 and the tool doesn't work!"`
    Verify Stage 1 classifies it as
    `Category: Billing / Sentiment: Frustrated`. Verify Stage 2 detects
    the \$120 amount exceeds the \$20 policy limit. Verify Stage 3 /
    Ticket Prompt triggers the escalation flow, generates the
    standardized ticket, and provides the customer sign-off message.
    Copy the ticket summary and save it to `conversations_portfolio.md`.
-   Confirm that across all scenarios the AI maintains empathetic tone,
    does not hallucinate outside the policy manual, and delivers clean
    structured outputs at every stage.

## Exercise 5 --- Write Documentation, Record Loom Video & Push Deliverables to GitHub

**Task:** Write the chatbot system documentation with a Mermaid.js flow
diagram, record a 3--4 minute Loom walkthrough of the full prompt chain
in action, organize all project files, and push them to a public GitHub
repository.

### Answer --- Setup Steps

-   Create a markdown file named `chatbot_documentation.md`. Write a
    description of the chatbot system instructions, target personas, and
    security guardrails. Add a Mermaid.js diagram mapping the logical
    routing:

``` mermaid
graph TD
UserQuery[Customer Query] --> Classifier[Intent Classifier Stage 1]
Classifier -->|Category: Billing / Account / Tech Support| PolicyCheck{Check Policy Limits}
PolicyCheck -->|Under $20 Limit / Standard Query| Responder[CARE Responder Stage 2]
PolicyCheck -->|Over $20 Limit / Urgent Escalation| Escalator[Escalation Ticket Prompt]
Responder --> Draft[Draft Reply]
Draft --> Verification[Reflection Verification Stage 3]
Verification -->|Approved| Deliver[Send Reply to Customer]
Verification -->|Flagged Violation| Escalator
Escalator --> Human[Human Support Queue]
```

-   Open Loom and sign in. Configure screen and webcam settings. Record
    a 3--4 minute video covering: the project name and prompt chaining
    architecture (0:00--0:45), the support prompt library and CARE
    framework explanation (0:45--2:00), a live ChatGPT demo pasting the
    Classifier and CARE Responder prompts and running Scenario C showing
    the \$120 escalation trigger (2:00--3:15), and the GitHub repository
    files (3:15--3:45). Save the recording, set sharing to public, and
    copy the URL.
-   Create a local folder named `prompt-engineering-support-assistant`.
    Move the following files into the folder:
    -   `support_prompt_library.md` --- all prompt templates.
    -   `conversations_portfolio.md` --- 3 scenario transcripts.
    -   `chatbot_documentation.md` --- system manual + Mermaid.js
        flowchart.
    -   `README.md` --- objectives, Loom video URL, and step-by-step
        setup guide.
-   Open a terminal inside the folder and run:

``` bash
git init
git add .
git commit -m "Initialize Prompt Engineering Support Assistant project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/prompt-engineering-support-assistant.git
git push -u origin main
```

-   Verify all files are visible and correctly rendered on GitHub,
    including the Mermaid.js flowchart in `chatbot_documentation.md`.
