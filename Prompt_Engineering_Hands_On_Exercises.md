# Prompt Engineering Hands-On Exercises

## Exercise 1 --- Set Up ChatGPT Workspace and Draft Naive (Before) Prompts

**Task:** Register or log into ChatGPT, initialize a clean workspace,
and draft and execute six naive (Before) prompts --- one for each
content type --- to establish a baseline for quality comparison.

### Answer --- Setup Steps

-   Open your web browser and navigate to chatgpt.com. Sign in with your
    free OpenAI account or register a new account if you do not have
    one.
-   Click the New Chat button in the top-left sidebar to open a clean
    chat thread, ensuring no previous conversation context interferes
    with your outputs.
-   Open a text editor on your local computer (e.g., Notepad, VS Code)
    and create a scratch file named `before_prompts.txt`.
-   Draft six naive prompts --- simple, single-sentence commands with no
    role, context, or style constraints --- one for each content type:
    -   **Blog Post:** Write a blog post about why remote work is good.
    -   **LinkedIn Post:** Write a LinkedIn post about learning prompt
        engineering.
    -   **Email Campaign:** Write a sales email promoting our new water
        bottle.
    -   **Instagram Caption:** Write an Instagram caption for a picture
        of a coffee cup.
    -   **YouTube Script:** Write a YouTube video script about how to
        start a business.
    -   **Product Description:** Write a product description for a
        wireless mouse.
-   Enter each naive prompt into ChatGPT one by one and copy the output
    text into your scratch file. These represent your Before outputs.
    Notice how they are often generic, verbose, and use cliché language.

## Exercise 2 --- Design the Optimized (After) Prompts Using Assigned Techniques

**Task:** Redesign your prompts using the six advanced techniques
assigned per content type --- RGCCO + Style Transfer for Blog Post,
Role + Zero-Shot for LinkedIn Post, One-Shot for Email Campaign,
Few-Shot for Instagram Caption, Role + RGCCO for YouTube Script, and
Few-Shot for Product Description --- and save all templates as your
Prompt Library.

### Answer --- Setup Steps

-   **Task 1 --- Blog Post (RGCCO Framework + Style Transfer):** Find a
    short reference text from a popular blog post whose style you
    admire. Construct a prompt defining the Role (expert blog writer),
    Goal (write a blog post), Context (benefits of remote work for B2B
    managers), Constraints (no corporate fluff, active voice, short
    paragraphs), and Output Format (H1 title, H2 sections, bulleted
    takeaways). Inject the Style Transfer instruction:
    `"Write in the style of the following text: [Insert Reference Text]"`.
-   **Task 2 --- LinkedIn Post (Role Prompting + Zero-Shot):** Instruct
    ChatGPT:
    `"Act as an expert Social Media Copywriter specializing in tech careers. Write a LinkedIn post about [Insert Topic]..."`
    Include strict constraints: under 150 words, no more than 2 emojis,
    and a single sentence hook.
-   **Task 3 --- Email Campaign (One-Shot Prompting):** Provide ChatGPT
    with one high-performing email layout example using role and context
    instructions. Structure the prompt around the example email template
    and then request:
    `"Now, write a B2B sales email promoting our new [Insert Product/Offer]."`
-   **Task 4 --- Instagram Caption (Few-Shot Prompting):** Draft 3
    different examples of engaging Instagram captions incorporating
    hooks, emojis, and grouped hashtags. Input these examples into your
    prompt so ChatGPT learns the exact structure and spacing required
    for `[Insert Image Description]`.
-   **Task 5 --- YouTube Video Script (Role Prompting + RGCCO):**
    Construct a detailed RGCCO prompt setting the Role to
    `"Professional YouTube Video Creator"`. Under Output Format, specify
    a split-column markdown layout with Left Column:
    `[Visual/Camera Cue]` and Right Column: `[Spoken Voiceover Script]`
    for the topic `[Insert Goal]` about `[Insert Topic]`.
-   **Task 6 --- Product Description (Few-Shot Prompting):** Create 2
    examples showing a raw list of technical specifications transformed
    into an emotionally compelling product description highlighting
    consumer benefits. Then request the same for `[Insert Specs]`.
-   Save all six prompt configurations in a draft file named
    `prompt_library.md`. These will form the core of your Prompt Library
    (REQ-003).

## Exercise 3 --- Execute Optimized Prompts and Capture Generated Content

**Task:** Run all six optimized prompt templates in ChatGPT by filling
in the bracketed variables with actual marketing copy details, review
and refine outputs as needed, and save all final generated content.

### Answer --- Setup Steps

-   Navigate back to your ChatGPT chat thread and open your
    `prompt_library.md` file.
-   For each of the six optimized prompt templates, replace the
    bracketed variables with actual marketing copy details:
    -   **Topic:**
        `"Why Remote Work Boosts B2B Software Engineering Efficiency"`
    -   **Product:** `"Apex Hydro 1-Liter Insulated Sport Bottle"`
    -   **YouTube Topic:**
        `"3 High-Income Skills You Can Self-Learn in 2026"`
-   Send each filled prompt to ChatGPT and copy the output.
-   If the output is cut off mid-sentence, type `"continue"` in the
    chatbox. ChatGPT will resume printing where it left off.
-   Review the outputs. If they do not meet all your constraints (e.g.,
    they still contain generic buzzwords or exceed word counts), refine
    the constraints in your prompt and execute again.
-   Once satisfied, copy all final outputs and save them in a markdown
    file named `generated_content.md` (REQ-004).

## Exercise 4 --- Create the Quality Comparison Table and Write the Improvement Report

**Task:** Compile a Before vs After Quality Comparison Table evaluating
all six content tasks across four dimensions (Relevance, Tone,
Formatting, Length) on a 1--5 scale, then write a Prompt Improvement
Report providing a qualitative breakdown for each task.

### Answer --- Setup Steps

-   Open your document editor and structure a markdown table with
    columns: Content Task, Prompt Version, Relevance (1-5), Tone (1-5),
    Formatting (1-5), Length (1-5), and Total Score /20.
-   Evaluate each of the six tasks for both the Before (Naive) and After
    (Optimized) versions. Grade each output on a scale of 1 (Poor) to 5
    (Excellent) per dimension. For example, the Blog Post Before might
    score 10/20 while the After scores 20/20 (REQ-005).
-   Save the completed comparison table inside your
    `improvement_report.md` file.
-   For each of the six tasks, write a short qualitative analysis under
    four headings:
    -   **Objective:** What was the target goal?
    -   **The Issue with the Before Prompt:** Why was the naive prompt
        insufficient?
    -   **The After Strategy:** Which prompt engineering techniques did
        you apply?
    -   **Quality Comparison Summary:** Explain the score difference
        from your comparison table (REQ-006).
-   Save and finalize the `improvement_report.md` file containing both
    the full comparison table and all six narrative task reports.

## Exercise 5 --- Record Loom Walkthrough Video and Publish All Deliverables to GitHub

**Task:** Record a 3-to-4 minute Loom walkthrough video demonstrating
your prompt library and a live ChatGPT run, then organize and push all
four required markdown files to a public GitHub repository.

### Answer --- Setup Steps

-   Navigate to loom.com and log in. Launch the Loom desktop application
    or Chrome extension and configure Screen & Camera recording with
    your microphone active.
-   Plan and record a 3-to-4 minute walkthrough:
    -   **0:00--0:45:** Introduce yourself, state the project goal
        (Prompt Engineering Hands-On Course), and list the six content
        types and six techniques used.
    -   **0:45--2:00:** Show your `prompt_library.md` in your text
        editor. Highlight one complex prompt (e.g., the RGCCO Blog Post
        or Few-Shot Instagram prompt) and explain the structural
        elements.
    -   **2:00--3:00:** Switch to ChatGPT. Paste your optimized prompt
        template, fill in the parameters, and run it live on screen.
        Briefly highlight how the output conforms to your constraints.
    -   **3:00--3:45:** Review the Before vs After Comparison Table and
        conclude the video.
-   Stop the recording, set the Loom video to Public, and copy the share
    URL.
-   Create a local directory on your machine named
    `prompt-engineering-hands-on` and structure it with the following
    four markdown files:
    -   `prompt_library.md` --- 6 optimized parameter-driven prompt
        templates labeled with the techniques used.
    -   `generated_content.md` --- Raw ChatGPT outputs for all 6 tasks.
    -   `improvement_report.md` --- Quality comparison table and all 6
        narrative reports.
    -   `README.md` --- Project overview including your name, project
        title, objectives, the Loom video URL, and instructions on how
        to use the prompt templates.
-   Open a terminal inside the folder and run:

``` bash
git init
git add .
git commit -m "Initialize Prompt Engineering Hands-On project"
```

-   Go to github.com, click New Repository, name it
    `prompt-engineering-hands-on`, set visibility to Public, and click
    Create Repository. Then run the remote setup commands and push:

``` bash
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/prompt-engineering-hands-on.git
git push -u origin main
```

-   Verify that all four files render correctly on your public GitHub
    repository page (REQ-007).
