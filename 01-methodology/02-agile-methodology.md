# 04-agile-methodology.md: The Scrum Master's Playbook
*How we organize chaos into shipping software.*

## 1. The Hierarchy of Work (The Pyramid)
Imagine a project as a pyramid. At the top is the Vision, at the bottom is the Code. We slice it horizontally.

### 🏛️ Level 1: Themes (The "Why")
*   **Definition**: A high-level strategic area of focus. It spans multiple projects or strict periods.
*   **Duration**: Quarters or Years.
*   **Example**: "Financial Independence" or "Health & Fitness".

### 🚩 Level 2: Milestones (The "When")
*   **Definition**: A major checkpoint on the timeline that represents a "shippable" state of the product. It aggregates several Epics.
*   **Key Question**: "Can we sell/use it yet?"
*   **Duration**: 1-3 Months.
*   **Example (Project Spark)**:
    *   *Milestone 1*: **MVP** (I can track my own time).
    *   *Milestone 2*: **SaaS Ready** (I can invite a friend).

### 📚 Level 3: Epics (The "What")
*   **Definition**: A large body of work that can be broken down into many specific stories. It usually represents a specific **Feature Set**.
*   **Key Rule**: An Epic is too big to finish in one Sprint.
*   **Example (Project Spark)**:
    *   *Epic*: **"Authentication System"** (Includes: Login, Register, Forgot Password, OAuth).
    *   *Epic*: **"Reporting Engine"** (Includes: PDF Export, Charts, CSV).

### 📖 Level 4: User Stories (The "Value")
*   **Definition**: The smallest unit of work that delivers **value** to the user.
*   **Format**: "As a [User], I want [Feature], so that [Benefit]."
*   **Key Rule**: must be "INVEST" (Independent, Negotiable, Valuable, Estimable, Small, Testable).
*   **Duration**: 1-3 Days.
*   **Example**: "As a User, I want to click 'Start' to begin a timer."

### 🔧 Level 5: Tasks (The "How")
*   **Definition**: The technical steps to complete a User Story. The user doesn't care about these; the developer does.
*   **Example**: "Create database migration for Timer table", "Design Figma Button component".

---

## 2. The Container of Time (The Sprint)
If the Hierarchy is "Space", the Sprint is "Time".

*   **Definition**: A fixed time-box (usually 2 weeks) where we commit to a specific set of User Stories.
*   **The Golden Rule**: **Scope is variable, Time is fixed.** You never extend the Sprint date. You cut the features if you're running late.
*   **The Rituals**:
    1.  **Planning**: We pick stories from the Backlog and put them in the Sprint.
    2.  **Daily Standup**: "What did I do? What will I do? Blockers?"
    3.  **Review**: Show the working software (Demo).
    4.  **Retrospective**: How do we work better next time?

---

## 3. Concrete Example: Organizing "Project Spark"

| Level | Name | Description |
| :--- | :--- | :--- |
| **Milestone** | **M1: The Self-Tracker** | The goal is a usable Personal App. |
| **Epic** | **Epic-01: Poly-Structure** | The data model that allows flexible tagging. |
| **Story** | **Issue-002: Schema Design** | "As a dev, I need the DB to support tags." |
| **Task** | **Task: Prisma Migration** | Run `npx prisma migrate dev`. |

## 4. How YOU should work (The Solo-Agile Flow)
Since you are both the Product Owner and the Developer:
1.  **Wear the PO Hat**: Write the Story in `documentation/github-issues`. Define "Acceptance Criteria".
2.  **Wear the Scrum Master Hat**: Put it in the "Sprint" (Decide to do it this week).
3.  **Wear the Developer Hat**: Write the code.
4.  **Wear the QA Hat**: Read the "Acceptance Criteria". Did you pass?
5.  **Close the Issue**.