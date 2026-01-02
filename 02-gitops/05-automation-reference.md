# The Glass Factory Engine

*Reference for the automation suite.*

## 1. Capabilities

1.  **Scaffolding**: Create standard folder structures.
2.  **Sync**: Ensure local state matches GitHub remote.
3.  **Audit**: Report on non-compliance (missing READMES, wrong folder names).

## 2. Architecture

*   **Language**: Python 3.10+
*   **Entry**: `src/main.py`
*   **Dependencies**: `gh` CLI

## 3. Usage

```bash
python3 src/main.py create <project>
python3 src/main.py sync-github <project>
```
