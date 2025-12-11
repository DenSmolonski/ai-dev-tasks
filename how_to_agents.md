# AGENTS.md Configuration

> Configure project-specific instructions for Ona Agent using AGENTS.md files.

AGENTS.md provides a dedicated, predictable place to give Ona Agent project-specific instructions. Ona automatically loads this file into context for every conversation, making it ideal for documenting project conventions, commands, and guidelines.

## What is AGENTS.md?

[AGENTS.md](https://agents.md/) is a readme for agents—a standardized way to provide instructions that help AI agents work effectively on your project. When present in your repository, Ona Agent automatically pulls this file into context at the start of every conversation.

## Creating an AGENTS.md file

Create an `AGENTS.md` file in your repository root to provide project-specific guidance to Ona Agent.

### Basic structure

```markdown  theme={null}
# Project Guidelines

## Common Commands
- `npm test` - Run the test suite
- `npm run build` - Build for production
- `npm run dev` - Start development server

## Key Files
- `src/components/` - Reusable UI components
- `src/utils/` - Utility functions
- `config/` - Configuration files

## Code Style
Follow the guidelines in CONTRIBUTING.md
```

### What to include

**Common commands and workflows:**

* How to test or rebuild generated code
* Development server startup commands
* Build and deployment processes
* Linting and formatting commands

**Project structure and key files:**

* Important directories and their purposes
* Entry points and configuration files
* Where to find specific types of code

**Code style and conventions:**

* Links to style guides or coding standards
* Naming conventions for files, functions, and variables
* Branch naming patterns and Git workflows

**Project-specific context:**

* Framework or technology choices
* Architecture decisions
* Dependencies and their purposes

## Example AGENTS.md

Here's an example from a real project:

```markdown  theme={null}
# Guidelines
For PR creation guidelines, check dev/docs/pull-request-guidelines.md
For Go modifications, follow the rules in dev/docs/go-styleguide.md
For frontend modifications, follow the rules in dev/docs/frontend.md
For vscode changes, follow the rules in dev/docs/vscode.md

# Feature work
- use feature branches from main for pushing work following this naming pattern:
  - [2-3 initials from git config user.name]/[[numeric-part-of-issue-ID?]-][2-3 words shorthand of the topics, separated by dashes]]
  - should not be more than 24 characters total
  - extract initials by taking first letter of each word from git user.name (e.g., "John Doe" → "jd", "Alice Smith Johnson" → "asj")
IMPORTANT: Always run git config user.name first to get the actual name - do not assume or guess the initials

# Code generation
- ALWAYS use leeway scripts to generate code, e.g. `leeway run api/def:generate` instead of running `buf generate` directly.
- Use `leeeway collect scripts` to understand what code generation scripts are available.
```

## Best practices

### Keep it concise

* Focus on essential information that affects how Ona Agent works on your project
* Avoid duplicating information that's already well-documented elsewhere
* Reference other files when appropriate rather than copying content

### Use emphasis for critical rules

* Use **IMPORTANT** or **ALWAYS** in all caps to highlight critical requirements
* Bold key terms and commands for better readability
* Use bullet points for easy scanning

### Reference external documentation

* Link to existing style guides, contributing guidelines, or architecture docs
* Point to specific files rather than duplicating their content
* Keep the AGENTS.md file as a navigation hub

### Make it actionable

* Provide specific commands rather than general descriptions
* Include exact file paths and naming conventions
* Give concrete examples of branch names, commit messages, etc.

## How Ona Agent uses AGENTS.md

### Automatic loading

* Ona Agent automatically reads AGENTS.md at the start of every conversation
* The content becomes part of the agent's context for the entire session
* No additional commands or setup required

### Context integration

* Instructions from AGENTS.md influence all of Ona Agent's responses
* The agent will follow the guidelines when making code changes
* Commands and conventions are applied consistently across tasks

### File references

* When you reference other files in AGENTS.md, Ona Agent will read them as needed
* This allows you to keep the main file concise while providing detailed guidance
* The agent understands the project structure through these references

## Updating AGENTS.md

### Version control

* Commit AGENTS.md changes like any other project file
* Include updates in pull requests when changing project conventions
* Document significant changes in commit messages

### Team collaboration

* Ensure all team members understand the AGENTS.md conventions
* Update the file when project structure or processes change
* Review AGENTS.md during onboarding to help new team members

### Iterative improvement

* Monitor how well Ona Agent follows the guidelines
* Refine instructions based on agent behavior and team feedback
* Add emphasis (IMPORTANT, ALWAYS) for frequently missed requirements

## Troubleshooting

### Agent not following guidelines

If Ona Agent isn't following your AGENTS.md instructions:

* Check that the file is named exactly `AGENTS.md` in the repository root
* Verify the instructions are clear and specific
* Add emphasis (bold, ALL CAPS) to critical requirements
* Consider breaking complex instructions into smaller, actionable steps

### Guidelines being ignored

If specific guidelines are consistently ignored:

* Move the most important rules to the top of the file
* Use stronger emphasis (IMPORTANT, ALWAYS) for critical requirements
* Provide concrete examples rather than abstract descriptions
* Reference specific files or commands rather than general concepts

### File not loading

If AGENTS.md doesn't seem to be loaded:

* Ensure the file is in the repository root directory
* Check that the filename uses the exact spelling: `AGENTS.md`
* Verify the file contains valid markdown content
* Start a new conversation to ensure the latest version is loaded

## Next steps

* Create an AGENTS.md file in your repository root
* Start with basic project information and common commands
* Iterate based on how well Ona Agent follows your guidelines
* [Learn about slash commands](/ona/slash-commands) for organization-wide prompts

Need help setting up AGENTS.md for your project? Reach out to your account manager if you're an enterprise customer.


---

> To find navigation and other pages in this documentation, fetch the llms.txt file at: https://ona.com/docs/llms.txt
