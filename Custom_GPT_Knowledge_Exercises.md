# Custom GPT Knowledge Files - 3-Point Explanation

## Exercise 1 - Prepare and Upload Knowledge File(s)

1. Prepare a clean source file such as a policy, FAQ, or process guide for the GPT to use.
2. Organize it with clear headings and sections and avoid scanned-only content so information can be retrieved properly.
3. Upload the file to the GPT builder's Knowledge section and confirm the upload is successful.

## Exercise 2 - Modify Instructions for Knowledge Priority

1. Update the instructions so uploaded knowledge files are the GPT's primary information source.
2. Tell the GPT to clearly state when requested information is not covered by the uploaded files.
3. This keeps responses aligned with approved documents instead of unsupported information.

## Exercise 3 - Add Anti-Hallucination Rules

1. Instruct the GPT never to invent facts that are not present in the uploaded knowledge documents.
2. Require the GPT to reference the relevant document or section when answering.
3. These rules improve accuracy and transparency by showing where the information came from.

## Exercise 4 - Test Factual and Misleading Questions

1. Test fully covered, partially covered, uncovered, and misleading questions to evaluate knowledge-file usage.
2. Check whether the GPT answers correctly, identifies missing information, and avoids accepting misleading assumptions.
3. Record results in test_qa_results.md with the question, expected answer, actual answer, and source-referenced status.

