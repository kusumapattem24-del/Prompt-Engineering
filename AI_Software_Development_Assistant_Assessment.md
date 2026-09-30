# AI Software Development Assistant --- Assessment Tasks & Answers

## Exercise 1 --- Set Up the Coding Workspace and Define the Target Project

**Task:** Initialize your ChatGPT development session and define the
software to be built --- a B2B "Task Tracker REST API" handling Users,
Tasks, and Status Management.

### Answer --- Setup Steps

-   Open your browser and navigate to https://chatgpt.com/, then log in
    to your account.
-   Click New Chat to clear the conversation context window before
    starting.
-   Confirm the scope of the project: a B2B Task Tracker REST API
    covering Users (Registration, Login, Auth tokens), Tasks (CRUD
    operations), and Status Management (Open, In Progress, Completed).
-   Verify you are working in a clean workspace before running any
    prompts (REQ-001).

## Exercise 2 --- Generate Requirements, Schema, and Controllers

**Task:** Use Least-to-Most prompting to generate software requirements
and user stories, then design SQL schemas, and finally generate route
controllers using the CRISPE framework.

### Answer --- Setup Steps

-   **Least-to-Most Requirements Prompt:** "Act as a Business Analyst.
    We want to design a backend REST API named 'Task Tracker API'.
    First, outline the system architecture scope and write 3 core B2B
    user stories (for User Signup, Task Creation, and Task Updates) with
    acceptance criteria. Do not write database schemas or backend code
    yet." Save the output to `srd_draft.txt` (REQ-001).
-   **SQL Database Schema Prompt:** Instruct ChatGPT to generate
    relational SQL table schemas for users (id, name, email,
    password_hash, created_at) and tasks (id, user_id, title,
    description, status, due_date, created_at), including NOT NULL,
    UNIQUE, FOREIGN KEY, and PRIMARY KEY constraints, with raw DDL SQL
    output (REQ-003).
-   **CRISPE Coding Prompt:** Following the CRISPE framework (Capacity,
    Recipient, Instruction, Style, Parameters, Evaluation), instruct
    ChatGPT to act as a Senior Backend Software Engineer and write route
    controller logic in Node.js/Express or Python/FastAPI for POST
    /api/v1/tasks and GET /api/v1/tasks/:id, following DRY/SOLID
    principles, using raw SQL (no ORM), with inline comments (REQ-002,
    REQ-004). Save the code draft in a local folder named
    `code_repository/`.

## Exercise 3 --- Run Secure Code Reflection and Debugging

**Task:** Audit your generated controllers for security exploits (such
as SQL injection) using a reflection prompt, and verify the refactored
output uses parameterized queries.

### Answer --- Setup Steps

-   Copy a mock vulnerable endpoint (e.g., a `/api/v1/login` route built
    with string-concatenated SQL) into ChatGPT as the code to audit.
-   **Secure Reflection Prompt:** "Act as a Security Auditor. Scan the
    code block below for security vulnerabilities (e.g., SQL Injection,
    unhandled crashes). Identify the issue, explain the risk, and write
    a refactored, secure version of this endpoint using parameterized
    SQL queries and try/catch blocks" (REQ-005, TR-003).
-   Run the prompt in ChatGPT and verify the output replaces the
    vulnerable query with a parameterized query, e.g.:

``` text
db.query("SELECT * FROM users WHERE email = ? ...", [email, password])
```

## Exercise 4 --- Generate Documentation, Tests, and Compile Deliverables

**Task:** Generate Swagger/OpenAPI documentation and unit tests for your
endpoints, then compile all outputs into structured Markdown deliverable
files.

### Answer --- Setup Steps

-   **API Documentation Prompt:** Generate Swagger/OpenAPI YAML
    documentation for POST /api/v1/tasks and GET /api/v1/tasks/:id,
    including request schema, 200 success response, and 400 error
    response blocks (REQ-006).
-   **Unit Test Prompt:** Act as a QA Automation Engineer and write 2
    unit tests in Jest/Supertest (or Python PyTest) validating
    successful task creation (asserts status 201) and getting a task
    with an invalid ID (asserts status 404) (REQ-006).
-   Create the following four files (TR-001):
    -   `api_documentation.md` --- containing your Swagger YAML block.
    -   `test_cases.md` --- containing your unit tests and a QA test
        matrix table.
    -   `prompt_library.md` --- containing your exact CRISPE,
        Least-to-Most, and Reflection prompt templates with parameter
        variables.
    -   `software_requirement_document.md` --- containing the user
        stories, SQL scripts, and final code controllers.

## Exercise 5 --- Record Loom Video and Push Deliverables to GitHub

**Task:** Record a 3-to-4-minute Loom video demonstrating your workspace
and a live secure reflection code review, then organize and push all
deliverables to a public GitHub repository.

### Answer --- Setup Steps

-   Log in to Loom at https://www.loom.com/ and configure screen and
    webcam recording (REQ-008).
-   Follow this structured recording timeline:
    -   **0:00 -- 0:45:** State the project name (AI Software
        Development Assistant) and explain the Least-to-Most prompting
        pipeline.
    -   **0:45 -- 2:00:** Show your local folder files
        (`code_repository/` and markdown files) and explain the CRISPE
        variables.
    -   **2:00 -- 3:15:** Open ChatGPT and paste your Secure Reflection
        Prompt live with the vulnerable login route; show ChatGPT
        refactoring the code to block SQL injection.
    -   **3:15 -- 3:45:** Show the unit tests and conclude the video.
-   Ensure the Loom video sharing settings are set to "Anyone with the
    link can view."
-   Create a local directory named `prompt-engineering-developer` and
    move in: `software_requirement_document.md`, `api_documentation.md`,
    `test_cases.md`, `prompt_library.md`, `code_repository/`, and
    `README.md` (title, objectives, your name, and the Loom video URL)
    (REQ-007, TR-001).
-   Open a terminal inside the folder and run:

``` bash
git init
git add .
git commit -m "Initialize Prompt Engineering Developer project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/prompt-engineering-developer.git
git push -u origin main
```

-   Confirm your repository is set to public and viewable from an
    incognito browser tab.
