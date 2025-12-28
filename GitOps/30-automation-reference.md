# 30-automation-reference.md: The Glass Factory Engine
*How we automate the creation of order from chaos.*

## 1. The "Why"
We do not manually click buttons in GitHub. We script the infrastructure.
This ensures **Reproducibility**, **Speed**, and **Standardization**.

## 2. The Script Inventory

### 2.1 `sync-smart-metadata.sh`
*   **Location**: `active-projects/[project-name]/scripts/`
*   **Purpose**: Bootstraps a repository with our standard Label Taxonomy and populates the Project Board.
*   **Metadata Used**:
    *   **Labels**: Standard colors (Red for Critical, Blue for Features).
    *   **Project Field IDs**: Uses `gh project item-add` logic.
*   **Logic**:
    *   Iterates through all `.md` files in `planned/` and `ongoing/`.
    *   **CRITICAL**: Matches Local File to GitHub Issue by **Exact Title**.
    *   If Title matches -> Updates Labels/Body.
    *   If No Match -> **Creates New Issue**.
    *   *Warning*: Do not rename local titles without renaming GitHub issues first, or you will create duplicates.
*   **Logic Flow**:
    1.  **Recursive Scan**: Finds all `.md` files in `planned/`, including Milestone subfolders.
    2.  **Frontmatter Parsing**: Extracts `title`, `type`, `priority`, and `milestone` from YAML.
    3.  **Idempotency Check**: Checks for duplicates (`gh issue list`).
    4.  **Sync Action**:
        *   **If Exists**: Updates Labels, Milestone, and uses GraphQL to set **Issue Type**.
        *   **If New**: Creates Issue, sets metadata, and links to **Project Board**.

### 2.2 `create-project-template.sh` (The Generator)
*   **Location**: `_standards_guidelines/GitOps/scripts/`
*   **Purpose**: Creates a NEW blank project structure for any future idea (Blackbird, Nexus).
*   **Capabilities**:
    *   Creates folder structure (`documentation`, `codebase`, `scripts`).
    *   Copies the `sync` scripts.
    *   Creates default READMEs.

## 3. GitHub Metadata Reference
(See `00-github-metadata-reference.md` for raw IDs).

## 4. How to use `gh` CLI for Project V2
*   **List Projects**: `gh project list --owner [org]`
*   **Inspect Fields**: `gh project field-list [number] --owner [org]`
*   **Add Item**: `gh project item-add [number] --owner [org] --url [issue-url]`
