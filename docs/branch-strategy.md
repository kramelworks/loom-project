# Loom Branch Strategy

This document defines the official git workflow for Loom.

---

# Main Branches

## main

Purpose:
- production-ready code only

Rules:
- protected branch
- direct commits are forbidden
- merge only from release or hotfix

---

## develop

Purpose:
- integration branch
- all completed work lands here first

Rules:
- protected branch
- merge only via Pull Request

---

# Supporting Branches

## feature branches

Used for:
- new features
- enhancements

Pattern:
feature/LOOM-XXX-description

Examples:
feature/LOOM-101-user-auth
feature/LOOM-205-content-editor

Target:
develop

---

## bugfix branches

Used for:
- defect corrections

Pattern:
bugfix/LOOM-XXX-description

Example:
bugfix/LOOM-310-login-timeout

Target:
develop

---

## release branches

Used for:
- release preparation
- stabilization

Pattern:
release/vX.Y.Z

Example:
release/v0.2.0

Flow:
develop -> release -> main

---

## hotfix branches

Used for:
- urgent production fixes

Pattern:
hotfix/vX.Y.Z

Example:
hotfix/v0.2.1

Flow:
main -> hotfix -> main + develop

---

# Merge Strategy

Default:
- squash merge

Reason:
- cleaner history
- easier rollback

---

# Commit Convention

Pattern:
type: description

Examples:
feat: add user authentication
fix: correct login validation
docs: update roadmap
refactor: simplify auth service