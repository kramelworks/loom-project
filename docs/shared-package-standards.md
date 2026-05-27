# Loom Shared Package Standards

This document defines the standards for shared packages in Loom.

---

# Goals

Shared packages exist to:
- reduce duplication
- standardize contracts
- centralize reusable logic
- improve consistency across repositories

Rules:
- packages must be isolated
- packages must be focused
- packages must avoid business coupling

---

# Package Scope

Official scope:

@loom/*

Examples:
- @loom/types
- @loom/contracts
- @loom/utils
- @loom/config

Registry:
GitHub Packages

---

# Shared Packages

## @loom/types

Purpose:
Shared domain types and interfaces.

Responsibilities:
- entity types
- enums
- shared interfaces
- value object types

Examples:
User
ContentType
Role

Rules:
- no runtime logic
- no infrastructure concerns
- no API transport concerns

Allowed:
types only

Forbidden:
services
database logic
HTTP logic

---

## @loom/contracts

Purpose:
API contracts and DTOs.

Responsibilities:
- request DTOs
- response DTOs
- API schemas
- validation schemas

Examples:
CreateUserRequest
ContentResponse

Rules:
- transport-safe only
- backend owns contracts
- frontend consumes contracts

Preferred:
zod schemas

---

## @loom/utils

Purpose:
Reusable generic utilities.

Responsibilities:
- slug generation
- date formatting
- string helpers
- validation helpers

Rules:
- generic only
- framework agnostic
- no business logic

Forbidden:
domain rules
application logic

---

## @loom/config

Purpose:
Shared engineering configuration.

Responsibilities:
- eslint config
- prettier config
- tsconfig presets
- shared tooling config

Examples:
@loom/config/eslint
@loom/config/tsconfig

---

# Package Structure

Standard structure:

src/
├── index.ts
├── types/
├── utils/
└── tests/

Rules:
- explicit exports
- avoid deep public paths

Preferred:
@loom/utils

Avoid:
@loom/utils/src/internal/helpers

---

# Dependency Rules

Allowed:

applications
→ shared packages

Forbidden:
shared packages
→ applications

Forbidden:
circular dependencies

---

# Versioning Strategy

Standard:
Semantic Versioning

Examples:
1.0.0
1.1.0
1.1.1

Rules:
- breaking changes → MAJOR
- new features → MINOR
- fixes → PATCH

---

# Publishing Strategy

Registry:
GitHub Packages

Publishing:
automated CI pipeline

Trigger:
merge to main

---

# Ownership

Backend team owns:
- @loom/contracts
- @loom/types

Platform/Engineering owns:
- @loom/config
- @loom/utils

---

# Testing Standards

Required:
unit tests for runtime packages

Optional:
types-only packages

---

# Documentation Standards

Each package must include:
- README
- usage examples
- public API documentation

---

# Future Shared Packages

Possible future packages:
- @loom/sdk
- @loom/ui
- @loom/testing
- @loom/eslint-plugin

---

# Design Principles

Shared packages must be:
- stable
- minimal
- reusable
- framework-light