# Loom Backend Project Structure

This document defines the backend structure for Loom.

Repository:
loom-api

Stack:
- TypeScript
- NestJS

Architecture:
- Clean Architecture
- Modular Monolith
- Feature-first

---

# High-Level Structure

src/
├── modules/
├── shared/
├── infrastructure/
├── config/
└── main.ts

---

# Modules

Each business domain lives inside modules/.

Example:

src/
 └── modules/
      └── users/

Rules:
- modules are isolated
- modules own their domain
- communication via application layer only

---

# Module Structure

Example:

src/modules/users/
├── domain/
├── application/
├── infrastructure/
├── presentation/
├── contracts/
└── tests/

---

# Domain Layer

Purpose:
Core business rules.

Contents:
- entities
- value objects
- domain services
- repository interfaces
- domain events

Rules:
- no framework dependencies
- pure business logic only

---

# Application Layer

Purpose:
Use cases and orchestration.

Contents:
- use cases
- application services
- DTO mapping
- commands/queries

Rules:
- depends on domain only

Examples:
CreateUserUseCase
PublishContentUseCase

---

# Infrastructure Layer

Purpose:
External implementations.

Contents:
- database repositories
- ORM models
- external services
- providers

Examples:
PrismaUserRepository
AzureBlobStorageProvider

---

# Presentation Layer

Purpose:
HTTP/API exposure.

Contents:
- controllers
- routes
- request validation
- response mapping

Rules:
- no business logic

---

# Contracts Layer

Purpose:
Module-specific DTOs/contracts.

Rules:
- integrates with @loom/contracts
- transport-safe only

---

# Shared Folder

Purpose:
Cross-module reusable code.

Structure:

src/shared/
├── kernel/
├── utils/
├── types/
└── exceptions/

Rules:
- no business domain leakage

---

# Infrastructure Root

Purpose:
Global infrastructure concerns.

Structure:

src/infrastructure/
├── database/
├── cache/
├── messaging/
├── storage/
└── monitoring/

---

# Configuration

Structure:

src/config/
├── env/
├── database/
├── auth/
└── app/

Rules:
- centralized config
- typed config only

---

# Testing Structure

Inside each module:

tests/
├── unit/
├── integration/
└── fixtures/

Rules:
- unit tests required
- integration tests preferred

---

# Dependency Rules

Allowed:
presentation
→ application
→ domain

infrastructure
→ domain/application

Forbidden:
domain
→ infrastructure

presentation
→ database

---

# ORM Strategy

Initial ORM:
Prisma

Database support:
- SQLite (development)
- Azure SQL (production)

---

# API Organization

Base path:
/api/v1

Example:
/api/v1/users
/api/v1/content

---

# Future Evolution

Possible future extraction:
- auth-service
- content-service
- media-service

Current strategy:
modular monolith first