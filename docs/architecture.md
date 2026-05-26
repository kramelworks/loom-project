# Loom Architecture Principles

This document defines the architectural principles for Loom.

---

# Architectural Style

Loom follows a:

Modular Monolith (initially)

Why:
- easier for learning
- simpler deployment
- faster delivery
- easy future extraction to microservices

Future:
- service extraction allowed when needed

---

# Core Principles

## Clean Architecture

Every service must follow layer separation:

Domain
Application
Infrastructure
Presentation

Dependency rule:
outside depends on inside

---

## SOLID

All modules should respect:

- Single Responsibility Principle
- Open/Closed Principle
- Liskov Substitution Principle
- Interface Segregation Principle
- Dependency Inversion Principle

---

## API First

Backend contracts are defined first.

Priority:
Contracts
→ API
→ Frontend

Shared contracts live in:
@loom/contracts

---

# Backend Architecture

Stack:
- TypeScript
- NestJS

Structure:

src/
├── domain
├── application
├── infrastructure
└── presentation

Example:

src/
 └── users/
      ├── domain/
      ├── application/
      ├── infrastructure/
      └── presentation/

---

# Frontend Architecture

Stack:
- Next.js
- TypeScript

Pattern:
Feature-based modules

Example:

src/
 ├── features/
 ├── components/
 ├── services/
 └── shared/

---

# Shared Packages

Shared code lives in:

@loom/types
@loom/contracts
@loom/utils
@loom/config

Rules:
- no business logic
- reusable only

---

# Testing Strategy

Minimum:
- unit tests

Preferred:
- integration tests

Optional:
- e2e tests

---

# Database Strategy

Development:
- SQLite

Production:
- Azure SQL

Access:
Repository pattern only

Direct SQL outside repositories is forbidden.

---

# DevOps Principles

- trunk-based integration via develop
- CI required
- automated quality gates
- automated deployment

---

# Non-Goals

Not allowed:
- premature microservices
- tightly coupled modules
- business logic in controllers
- direct database access in controllers
