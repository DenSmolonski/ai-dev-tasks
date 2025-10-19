# Rule: Troubleshooting and Resolving Bugs

## Goal

To guide an AI assistant in systematically identifying, diagnosing, and resolving bugs. The process should be methodical, transparent, and follow best practices like test-driven development (TDD) to ensure a high-quality, stable fix.

## Process

1.  **Receive Bug Report:** The user provides an initial description of an issue, unexpected behavior, or error.
2.  **Ask Clarifying Questions:** Before attempting any fix, the AI *must* ask clarifying questions to gather sufficient detail. The primary goal is to get reproducible steps. Make sure to provide options in letter/number lists so the user can respond easily.
3.  **Formulate Reproduction Plan:** Based on the user's answers, state the exact steps you will take to try and reproduce the bug. Ask the user to confirm this plan.
4.  **Reproduce and Diagnose:** Attempt to reproduce the bug.
    * **If successful:** Report the successful reproduction. Investigate the root cause by analyzing code, logs, and application state.
    * **If unsuccessful:** Report the failure. Ask for more details or alternative steps. Do *not* proceed.
5.  **Propose Solution & Test Plan:** Once the root cause is identified, propose a specific solution. This proposal *must* include a testing plan (see "Solution & Verification Structure" below).
6.  **Implement Fix:** After the user approves the solution, implement the fix. This work should follow the "Task List Management" guidelines (e.g., breaking the fix into sub-tasks, waiting for user approval after each, etc.).
7.  **Verify and Commit:** After implementing the fix, run the full test plan (new tests and regression tests). Once all tests pass, generate the `git commit` command as per the guidelines.
8.  **Report Resolution:** Inform the user that the bug is fixed, briefly explain the root cause and the solution, and provide the final commit message.

## Clarifying Questions (Examples)

The AI should adapt its questions, but common areas to explore include:

* **Observed vs. Expected:** "Can you describe what you *expected* to happen, and what *actually* happened?"
* **Reproduction Steps:** "What are the *exact* steps, click-by-click, to make this bug appear? (e.g., 1. Go to page X, 2. Click button Y, 3. Type 'test' in field Z)"
* **Error Messages:** "Did you see any error messages on the screen or in the developer console? If so, please provide the full text."
* **Frequency:** "Does this bug happen...
    a) Every single time?
    b) Only sometimes?
    c) Only for specific data (e.g., a specific user, a specific item)?"
* **Environment:** "Where are you seeing this?
    a) On your local development machine?
    b) On the staging server?
    c) In production?"
* **Recency:** "Did this feature work correctly before? If so, do you know what might have changed recently?"

## Solution & Verification Structure

When proposing a fix, the plan should include these components:

1.  **Root Cause Analysis:** A brief (1-2 sentence) explanation of *why* the bug is happening (e.g., "The `calculate_total` function does not check if the `cart.items` array is empty, leading to a 'division by zero' error when calculating the average price.").
2.  **Proposed Solution:** A clear description of the code change (e.g., "I will add a guard clause at the top of the `calculate_total` function to return 0 if `cart.items` is empty.").
3.  **Files to be Modified:** A list of files that will be changed.
4.  **Testing Plan:** This is mandatory.
    * **New Test(s):** Describe the new unit/integration test(s) you will add. This test should *fail* before the fix is applied and *pass* after. (e.g., "Add a unit test `test_calculate_total_with_empty_cart` that asserts the function returns 0.").
    * **Regression Tests:** State that you will run the *full* existing test suite (e.g., `pytest`, `npm test`) to ensure the fix does not break any other functionality.

## Target Audience

Assume the AI is a **pair programmer** working with a human developer (the user). Communication must be precise, and no changes should be made without confirmation. The process must build confidence that the fix is correct and safe.

## Output

* **Primary Output:** Clear communication with the user at each step of the "Process."
* **Final Deliverables:**
    1.  The code diff/patch for the fix.
    2.  The new test(s) that cover the bug.
    3.  Confirmation that all tests (new and existing) are passing.

       
## Final instructions

1.  **NEVER** attempt a fix until you can reliably reproduce the bug.
2.  **ALWAYS** ask clarifying questions if the bug report is ambiguous.
3.  **ALWAYS** write a new test that captures the bug *before* finalizing the fix. This test should fail first, then pass.
4.  **ALWAYS** run the full regression test suite to check for side effects.
5.  **Follow the "Task List Management" protocol** for implementation (e.g., one sub-task at a time, wait for user approval).
