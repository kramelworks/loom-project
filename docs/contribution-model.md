# Loom Contribution Model

This document defines how contributors collaborate in the Loom project.

---

# Contribution Flow

Every contribution follows this workflow:

Issue
→ Branch
→ Development
→ Pull Request
→ Review
→ Merge
→ Release

---

# 1. Pick an Issue

Contributors must select an existing issue from the GitHub Project board.

Rules:
- issue must be assigned
- issue must be moved to "In Progress"

---

# 2. Create a Branch

Branch naming standard:

feature/LOOM-001-description
bugfix/LOOM-010-description
hotfix/LOOM-999-description

Examples:
feature/LOOM-101-user-auth
bugfix/LOOM-205-login-error

---

# 3. Development Rules

Contributors must:
- follow coding standards
- follow architecture guidelines
- write tests when applicable
- update documentation when required

---

# 4. Pull Request

PR must:
- reference the issue number
- explain the change
- include test evidence
- request at least one reviewer

Example:
Closes #101

---

# 5. Review Process

Reviewers validate:
- code quality
- architecture compliance
- tests
- documentation

Possible outcomes:
- approved
- changes requested

---

# 6. Merge Rules

Only approved PRs may be merged.

Merge strategy:
- squash merge

Branch target:
- develop

---

# 7. Releases

Only maintainers can create releases.

Release flow:
develop → release → main