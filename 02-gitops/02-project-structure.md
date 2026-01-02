# The GitOps Hierarchy

*Standardizing the physical organization of project artifacts.*

## 1. Directory Structure

```
project-root/
├── src/                # Source code (polyglot)
├── docs/               # Documentation (SDLC)
│   ├── planning/       # Product specs
│   ├── architecture/   # Technical design
│   └── operations/     # Runbooks
├── scripts/            # Automation
├── tests/              # Test suites
└── README.md           # Project metadata
```

## 2. Naming Conventions

*   **Files**: `kebab-case.md`
*   **Folders**: `lower-kebab-case`
*   **Branches**: `type/description` (e.g., `feature/add-login`)
