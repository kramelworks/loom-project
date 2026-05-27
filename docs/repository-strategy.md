# Loom Repository Strategy

This document defines the repository strategy for Loom.

---

# Strategy

Loom uses a multi-repository architecture.

Reason:
- clearer ownership
- simpler onboarding
- isolated CI/CD
- independent releases
- easier contributor experience

---

# Organization

GitHub Organization:
kramelworks

---

# Core Repositories

## loom-project

Purpose:
Project governance and documentation.

Responsibilities:
- roadmap
- RFCs
- architecture
- contribution process
- templates

---

## loom-api

Purpose:
Backend API.

Stack:
- TypeScript
- NestJS

Responsibilities:
- domain logic
- application services
- authentication
- persistence
- API exposure

---

## loom-web

Purpose:
Frontend admin application.

Stack:
- Next.js
- TypeScript

Responsibilities:
- admin UI
- forms
- dashboards
- authentication flow

---

## loom-shared-types

Purpose:
Shared domain types.

Package:
@loom/types

Responsibilities:
- entities
- enums
- value objects
- shared interfaces

Rules:
- no runtime logic

---

## loom-shared-contracts

Purpose:
Shared DTOs/contracts.

Package:
@loom/contracts

Responsibilities:
- request DTOs
- response DTOs
- API schemas

Rules:
- backend owns contracts
- frontend consumes contracts

---

## loom-shared-utils

Purpose:
Reusable utilities.

Package:
@loom/utils

Responsibilities:
- slug helpers
- date helpers
- formatting
- validation helpers

Rules:
- generic only
- no business logic

---

## loom-config

Purpose:
Shared configuration standards.

Package:
@loom/config

Responsibilities:
- eslint config
- prettier config
- tsconfig
- shared tooling

---

# Dependency Rules

Allowed:

loom-web
→ @loom/contracts
→ @loom/types
→ @loom/utils

loom-api
→ @loom/contracts
→ @loom/types
→ @loom/utils

Forbidden:
- frontend depending on backend
- shared packages depending on applications
- circular dependencies

---

# Package Registry

Strategy:
GitHub Packages

Scope:
@loom/*

Examples:
@loom/types
@loom/contracts
@loom/utils

---

# CI/CD Ownership

Each repository owns its own:
- pipeline
- tests
- releases
- deployment

---

# Release Strategy

Independent versioning.

Examples:
loom-api v0.2.0
loom-web v0.2.1

Shared packages:
semantic versioning

---

# Future Repositories

Possible future repos:
- loom-docs
- loom-sdk-js
- loom-cli
- loom-infra