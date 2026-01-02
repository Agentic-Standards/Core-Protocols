# 15-project-management.md: The Agile Taxonomy

## 1. Label Taxonomy (The Color Code)
We use a strict 3-part label system: `category:name`.

### 🚨 Priority (Red/Orange)
*   `priority:critical` (🔴 D4380D) - Must fix immediately. System down or MVP blocker.
*   `priority:high` (🟠 FA8C16) - Core feature request.
*   `priority:medium` (🟡 FAAD14) - Standard improvement.
*   `priority:low` (🟢 A0D911) - Nice to have / Polish.

### 📦 Type (Blue/Purple)
*   `type:feat` (🔵 1890FF) - New functionality.
*   `type:bug` (🟣 722ED1) - Something is broken.
*   `type:chore` (⚪ BFBFBF) - Setup, deps updates, refactoring.
*   `type:docs` (🔷 13C2C2) - Documentation only.

### 🚩 Milestone (Gold)
*   `milestone:m1` (One User MVP)
*   `milestone:m2` (Forgiveness)
*   `milestone:m3` (SaaS)
*   `milestone:m10` (Life OS)

### 🧩 Epic / Component (Teal)
*   `epic:auth`
*   `epic:ui`
*   `epic:backend`
*   `epic:devops`

## 2. GitHub Project Configuration
The Board must have these columns (Status):
1.  **Backlog**: Ideas and future tasks.
2.  **Ready**: Spec is clear, ready for dev.
3.  **In Progress**: Actively being coded.
4.  **Review**: PR open.
5.  **Done**: Merged and deployed.