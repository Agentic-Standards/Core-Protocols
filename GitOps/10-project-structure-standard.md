# 10-project-structure-standard.md: The GitOps Hierarchy
*Standardizing the physical organization of project artifacts to mirror the logical project management structure.*

## 1. The Core Philosophy
**"The Folder is the Vertical."**
We organize files by their **Milestone** (Vertical Hierarchy).
We organize context by **Labels** (Horizontal Dimensions: Themes, Domains).
This prevents deep nesting hell (e.g., `planned/frontend/M1/Epic1`) and keeps the roadmap clear.

## 2. Directory Structure
```
project-root/
├── .github/                 # GitHub specific configs
├── codebase/               # Source code (frontend, backend)
├── documentation/
│   ├── 00-project-charter.md
│   ├── 01-master-backlog.md
│   └── github-issues/
│       ├── planned/        # The Backlog (Source of Truth)
│       │   ├── M001: The Self-Tracker/
│       │   │   ├── 001-bootstrap.md
│       │   │   └── 002-data-model.md
│       │   ├── M002: The Forgiving Engine/
│       │   └── ...
│       ├── ongoing/        # Active Work (Symlinks or Moves)
│       │   ├── M001: The Self-Tracker/
│       │   └── ...
│       └── closed/         # Archive
│           └── M001: The Self-Tracker/
└── scripts/                # Automation
    ├── sync-smart-metadata.sh
    └── organize_issues.py
```

## 3. Naming Conventions

### 3.1 Milestone Folders
*   **Format**: `m[XXX]-[slug-title]` (Kebab-case)
*   **Example**: `m001-the-self-tracker`
*   **Why**:
    *   No spaces (better for scripting).
    *   Lowercase (Linux standard).

### 3.3 Hierarchy Numbering (The Decimal System)
To maintain order, we use a strict parent-child numbering code:
*   **Epic**: `E[M]01` (e.g., 201 = Milestone 2, Epic 1)
*   **Story**: `S[Epic].X` (e.g., 201.1 = Story 1 of Epic 201)
*   **Task/Test**: `T[Story].X` (e.g., 201.1.1)

## 4. Workflows

### 4.1 Planning Phase
1.  Create the Milestone Folder in `planned/`.
2.  Draft Markdown files with Frontmatter (YAML).
3.  Run `sync-smart-metadata.sh` to push to GitHub.

### 4.2 Execution Phase (Optional)
*   Move the file from `planned/` to `ongoing/` when work starts.
*   *Note*: Our sync scripts scan `planned/` by default. If moving files, ensure scripts are updated or symlinks are used.

### 4.3 Archive Phase
*   Move to `closed/` upon completion.

---
*This standard ensures that a new developer can understand the project chronology simply by browsing the file system.*
