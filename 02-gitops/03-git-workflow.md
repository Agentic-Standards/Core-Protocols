# Git Workflow Standard

## 1. Branching Model

*   **`main`**: Production-ready state. Protected.
*   **`develop`**: Integration branch (optional, for persistent beta).
*   **`feature/*`**: New work.
*   **`fix/*`**: Bug fixes.
*   **`chore/*`**: Maintenance.

## 2. Commit Messages

Format: `type(scope): subject`

*   `feat`: New feature
*   `fix`: Bug fix
*   `docs`: Documentation only
*   `style`: Formatting
*   `refactor`: Code change that neither fixes a bug nor adds a feature
*   `test`: Adding missing tests
*   `chore`: Maintain

## 3. Pull Requests

*   Must reference an Issue ID.
*   Must pass CI checks.
*   Must have 1 approval.
