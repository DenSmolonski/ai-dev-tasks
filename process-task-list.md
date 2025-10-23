# Task List Management

Guidelines for managing task lists in markdown files to track progress on completing a PRD

## Task Implementation
- **One parent task at a time:** Work on all sub-tasks of a single parent task together. Do **NOT** start the next parent task until you ask the user for permission and they say "yes" or "y".
- **Completion protocol:**  
  1. When you finish **all sub-tasks** of a parent task, immediately mark them as completed by changing `[ ]` to `[x]`.
  2. If **all** subtasks underneath a parent task are now `[x]`, follow this sequence:
    - **First**: Run the full test suite (`pytest`, `npm test`, `bin/rails test`, etc.)
    - **Clean up**: Remove any temporary files and temporary code before committing

  3. Once all the subtasks are marked completed and changes have been committed, mark the **parent task** as completed.
- Stop after completing all sub-tasks of a parent task and wait for the user's go-ahead to proceed to the next parent task.

## Task List Maintenance

1. **Update the task list as you work:**
   - Mark tasks and subtasks as completed (`[x]`) per the protocol above.
   - Add new tasks as they emerge.

2. **Maintain the "Relevant Files" section:**
   - List every file created or modified.
   - Give each file a one‑line description of its purpose.

## AI Instructions

When working with task lists, the AI must:

1. Regularly update the task list file after finishing all sub-tasks of a parent task.
2. Follow the completion protocol:
   - Mark each finished **sub-task** `[x]` after completing all sub-tasks of the parent task.
   - Mark the **parent task** `[x]` once **all** its subtasks are `[x]`.
3. Add newly discovered tasks.
4. Keep "Relevant Files" accurate and up to date.
5. Before starting work, check which parent task is next and work on all its sub-tasks.
6. After implementing all sub-tasks of a parent task, update the file and then pause for user approval before starting the next parent task.

