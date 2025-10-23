-----

# AI Agent Project Context: [Your Project Name]

**Purpose:** This document provides the high-level context, goals, and constraints for the project. Use this as your "source of truth" to avoid guessing and to ensure all generated code and recommendations align with the project's architecture and objectives.

---

## 1. Project Vitals

* **Project Name:** [Your Project Name]
* **Core Purpose (The "Why"):** [A 1-2 sentence description of the problem this project solves. e.g., "A tool to help remote teams track their quarterly goals (OKRs) in a simple, visual way."]
* **Key Features (The "What"):** [A bulleted list of the 3-5 most important features. e.g.,]
    * User authentication (Sign up, Login, Password Reset).
    * Create, Read, Update, Delete (CRUD) for Objectives and Key Results.
    * A visual dashboard showing progress for each team.
    * Invite team members to a workspace.

---

## 2. Guiding Principles & Constraints

[This is the most important section to prevent "guessing." These are your non-negotiable rules.]

* **Architecture:** [e.g., "Monolithic server-rendered app", "Serverless backend (Lambda) with a SPA frontend", "Microservices"]
* **Core Technologies (Must-Use):**
    * **Language:** [e.g., "TypeScript only"]
    * **Frontend:** [e.g., "React (Next.js App Router)"]
    * **Backend:** [e.g., "Node.js (NestJS)"]
    * **Database:** [e.g., "PostgreSQL with Prisma ORM"]
* **Styling:** [e.g., "Tailwind CSS. Do not use styled-components or regular CSS files."]
* **State Management:** [e.g., "Zustand for global state. Use React Context only for simple themes/auth."]
* **Code Style:** [e.g., "Follow Airbnb style guide. Use functional components with React Hooks. No class components."]
* **Key Prohibitions (Do-Not-Use):** [e.g., "Do not use Redux", "Do not use jQuery", "Do not write business logic directly in API controllers."]

---

## 3. Core Entities / Data Concepts

[A high-level list of the main "nouns" in your system. This helps the AI understand the data relationships without needing a full schema.]

* **User:** (Manages authentication, has a profile)
* **Workspace:** (Belongs to a User, contains multiple Teams and Projects)
* **Team:** (A group of Users within a Workspace)
* **Objective:** (The main goal, e.g., "Launch new website")
* **KeyResult:** (Measurable steps to achieve an Objective, e.g., "Get 10,000 signups")
* **[Other Entity]:** [e.g., "Task", "Comment", "Notification"]

---

## 4. Key User Journeys

[Simplified user flows. Describe the *goal*, not the click-by-click implementation.]

1.  **Onboarding Journey:**
    * A new user signs up with an email and password.
    * They create their first "Workspace" (e.g., "Acme Inc.").
    * They are taken to their new dashboard.
2.  **Core Action Journey (Creating an OKR):**
    * An authenticated user is on their dashboard.
    * They create a new "Objective" for the current quarter.
    * They then add 2-3 "Key Results" to that Objective.
    * The dashboard updates to show the new OKR.
3.  **Invitation Journey:**
    * A Workspace "Admin" navigates to the "Team" page.
    * They enter the email of a new team member.
    * The new member receives an invite link to join that specific Workspace.
