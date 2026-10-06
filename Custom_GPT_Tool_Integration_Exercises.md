# Custom GPT Tool Integration Exercises

## Exercise 1 - Enable a Tool

**Task:** Identify and enable a relevant tool for your GPT's use case.

### Answer - Setup Steps
- Select a tool matching your use case (for example, Code Interpreter for data-related GPTs).
- Enable it in the GPT builder's Capabilities section.

## Exercise 2 - Define Trigger and Non-Trigger Rules

**Task:** Write explicit rules for when the tool should and should not be used.

### Answer - Setup Steps
- Add: "Use [tool] only when the request requires live computation/data/external interaction."
- Add: "Do not use [tool] for simple questions answerable directly."

## Exercise 3 - Add Fallback Behavior

**Task:** Define what the GPT should do if the tool fails or returns no result.

### Answer - Setup Steps
- Add: "If the tool fails or returns no result, inform the user clearly and suggest an alternative."

## Exercise 4 - Test Tool-Required and Non-Tool Scenarios

**Task:** Trigger both a tool-required and a non-tool-required scenario and record results.

### Answer - Setup Steps
- Submit one query clearly requiring the tool and one that does not.
- Record in test_examples.md whether the tool was correctly triggered or correctly skipped.

