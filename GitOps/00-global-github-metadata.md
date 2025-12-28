# 00-global-github-metadata.md: The GitOps Dictionary
*A universal reference for GitHub Projects V2 Metadata & API Types.*

## 1. Core Field Types (`ProjectV2FieldType`)
When defining or querying fields via GraphQL/CLI, these are the immutable types.

| Type Name | CLI/JSON Representation | Usage Scenario |
| :--- | :--- | :--- |
| **Text** | `ProjectV2Field` | Short strings, Notes, Epics (if not using custom iterators). |
| **Number** | `ProjectV2Field` | Story Points, Complexity Scores (1-100), Budget. |
| **Date** | `ProjectV2Field` | Due Dates, Start Dates. |
| **Single Select** | `ProjectV2SingleSelectField` | **Status**, Priority, Size (T-Shirt Sizing). |
| **Iteration** | `ProjectV2IterationField` | Sprints (Start/End dates auto-calculated). |

## 2. Built-in Fields (Immutable)
Every V2 Project comes with these fields hardcoded. You cannot delete them, but you can hide them.

| Field Name | Description | Data Source |
| :--- | :--- | :--- |
| **Title** | The text displayed on the card. | Issue Title or Draft Issue text. |
| **Status** | The column storage. | Custom Options (Todo, Done). |
| **Assignees** | Who is working on it. | GitHub User Profile. |
| **Labels** | Taxonomy tags. | Repository Labels (Synced). |
| **Milestone** | Time-based grouping. | Repository Milestone (*Must include **Due Date** in Repo*). |
| **Repository** | Origin source. | The repo the issue belongs to. |
| **Linked Pull Requests** | Code connection. | PRs that reference the issue (shows as "Development"). |
| **Reviewers** | Code review status. | Users requested for PR review. |
| **Issue Type** | Nature of work. | Org-level Types (Task, Bug, Feature, Epic, Story, Test, Question). |

### 2.1 Recommended Status Columns
*   **Todo**: Default.
*   **In Progress**: Active (`status:wip`).
*   **In Review**: QA/Code Review (`status:review`).
*   **Blocked**: Impediment (`status:blocked`).
*   **Done**: Merged/Closed.

title: "Epic 1.1: Poly-Structure Data Model"
type: Epic
priority: High
milestone: "M001: The Self-Tracker"
assignee: "gadix1-tech"
tags:
  - theme:ignition
  - domain:database

### 2.2 Horizontal Dimensions (Labels)
*   **Themes**: Strategic pillars (e.g., `theme:forgiveness`, `theme:ignition`).
*   **Domains**: Technical areas (e.g., `domain:frontend`, `domain:database`, `domain:infra`).

## 3. Automation Patterns (CLI)

### 3.1 Inspecting a Project's Schema
To know which ID maps to "Status" for a specific project, you must query it.
```bash
# Get the Field List
gh project field-list [PROJECT_NUMBER] --owner [ORG] --format json
```

### 3.2 Parsing Single Select options
For "Status" or "Priority" fields, you need the `optionId`, not just the name.
```bash
# Extract settings for a Single Select field
gh project field-list [N] --owner [ORG] --format json | jq '.[] | select(.type == "ProjectV2SingleSelectField")'
```

### 3.3 Adding Items
Items are added by `contentId` (Issue ID) or created as Drafts.
```bash
# Add an existing Issue/PR
gh project item-add [PROJECT_NUMBER] --owner [ORG] --url [ISSUE_URL]
```

### 3.4 Validating Issue Metadata
If an issue looks "Empty" in the UI, check these fields:
*   **Milestone**: Does the Milestone object exist in the Repo? Does it have a `due_on` date?
    *   *Fix*: `gh api repos/[org]/[repo]/milestones -f title="M1" -f due_on="YYYY-MM-DD..."`
*   **Development**: Is there a linked Branch/PR?
    *   *Fix*: Push a branch with the issue number in the name or commit msg (e.g., `feature/issue-123`).
*   **Participants**: Who has commented/acted?
    *   *Fix*: Add a comment `gh issue comment [id] --body "..."`

### 3.5 Managing Issue Types (Task/Bug/Feature)
Issue Types are distinct from Labels. They must be set via GraphQL.

1.  **Create New Types (Organization Level)**:
    ```bash
    # Requires Org ID (NOT Repo ID)
    gh api graphql -f query='mutation { createIssueType(input: {ownerId: "[ORG_NODE_ID]", name: "Epic", description: "...", isEnabled: true}) { issueType { id } } }'
    ```

2.  **List Available Types**:
    ```bash
    gh api graphql -f query='query { repository(owner:"[ORG]", name:"[REPO]") { issueTypes(first:10) { nodes { id name } } } }'
    ```

3.  **Set Issue Type**:
    ```bash
    gh api graphql -f query='mutation { updateIssue(input: {id: "[ISSUE_NODE_ID]", issueTypeId: "[TYPE_ID]"}) { issue { issueType { name } } } }'
    ```

## 4. The "New Project" Playbook (Metadata Strategy)
When spinning up a new property (e.g., Nexus, Blackbird), follow this sequence to ensure 100% metadata health.

### Step 1: Organization Prep (One-Time)
1.  **Get Org ID**: `gh api graphql -f query='query { organization(login: "my-org") { id } }'`
2.  **Create Types**: Run the mutation to create `Epic`, `Story`, `Question` at Org level.

### Step 2: Repository Bootstrap
1.  **Metadata**: Set Description & Topics immediately.
    *   `gh repo edit [org]/[repo] --description "..." --add-topic "..."`
2.  **Milestones**: Create M001-M003 with *Due Dates*. Use 3-digit padding for sorting.
    *   `gh api repos/[org]/[repo]/milestones -f title="M001: The MVP" -f due_on="..."`

### 3.2 Issue Types (Vertical)
1.  **Epic** (`type:epic`): Large containers (e.g., "The Polys-Structure").
2.  **Story** (`type:story`): User Value Units (Checklists inside Epics).
3.  **Task** (`type:task` or `Issue XXX`):
    *   **Note**: Historically named "Issue XXX" in titles, but functionally are Tasks.
    *   Small, actionable engineering units (e.g., "Build Schema").
    *   We maintain "Issue" naming for legacy alignment.

### Step 3: Issue Injection
1.  **Script**: Run `sync-labels-and-issues.sh` to create issues and labels.
2.  **Link**: Ensure script calls `gh project item-add`.
3.  **Type**: Loop through created issues and set `issueType` (e.g., to "Task" or "Epic") using GraphQL.

### Step 4: First Task Cycle (Proof of Life)
1.  **Branch**: Create `chore/issue-1-init`.
2.  **Push**: Push to link "Development".
3.  **Comment**: "Started." to link "Participants".
