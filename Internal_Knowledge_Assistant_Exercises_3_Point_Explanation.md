# Internal Knowledge Assistant Exercises - 3-Point Explanation

## Exercise 1 - Gather Knowledge Files

1. Collect at least one policy document and one FAQ or process guide that the GPT will use as its approved knowledge source.
2. Clean and organize the documents using clear headings, sections, and readable content so information can be found easily.
3. Check that the files contain consistent information without conflicting rules, helping the GPT provide reliable answers.

## Exercise 2 - Build the Instruction Block

1. Define the GPT's role as an Internal Company Knowledge Assistant.
2. Set the scope so it answers only from uploaded documents and refuses questions that are unknown or outside the available knowledge.
3. Save the finalized instructions in instruction_block.md so the GPT has a clear and consistent operating framework.

## Exercise 3 - Add Behavior Rules and Guardrails

1. Instruct the GPT not to provide personal opinions, external knowledge, speculative answers, or unsupported information.
2. Require the GPT to avoid inventing information when an answer cannot be found in the uploaded documents.
3. Require references to the relevant document or section wherever applicable so users can verify the answer.

## Exercise 4 - Test the Three Coverage Scenarios

1. Test a fully covered question to confirm the GPT correctly answers using the uploaded documents.
2. Test partially covered and uncovered questions to confirm the GPT identifies missing information instead of guessing.
3. Record the results in test_results.md to verify that the GPT is accurate, reliable, and following its knowledge boundaries.

