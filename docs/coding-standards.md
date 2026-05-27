# Loom Coding Standards

This document defines the coding standards for Loom.

---

# General Principles

Code must be:
- readable
- maintainable
- testable
- explicit
- predictable

Priority:
clarity over cleverness

---

# Language Standards

Primary language:
TypeScript

Rules:
- strict mode enabled
- avoid any
- explicit return types preferred
- immutable by default

---

# Naming Conventions

## Files

Pattern:
kebab-case

Examples:
user-service.ts
create-user.dto.ts

---

## Classes

Pattern:
PascalCase

Examples:
UserService
CreateUserUseCase

---

## Interfaces

Pattern:
PascalCase

Examples:
UserRepository
ContentGateway

No "I" prefix.

Forbidden:
IUserRepository

---

## Variables

Pattern:
camelCase

Examples:
userId
contentType

---

## Constants

Pattern:
UPPER_SNAKE_CASE

Examples:
MAX_RETRY_COUNT

---

# Folder Conventions

Pattern:
feature-first

Backend example:

src/
 └── users/
      ├── domain/
      ├── application/
      ├── infrastructure/
      └── presentation/

Frontend example:

src/
 └── features/
      └── users/

---

# Clean Code Rules

Required:
- small functions
- single responsibility
- explicit naming
- avoid deep nesting
- avoid magic numbers
- avoid duplicated logic

Forbidden:
- business logic in controllers
- God classes
- hidden side effects

---

# Imports

Rules:
- absolute imports preferred
- avoid circular dependencies
- group imports logically

Order:
1. external
2. internal shared
3. local

---

# Error Handling

Rules:
- typed errors preferred
- never swallow exceptions
- meaningful error messages

Forbidden:
empty catch blocks

---

# Testing Standards

Minimum:
unit tests

Preferred:
integration tests

Test naming:
should_do_something_when_condition

Examples:
should_create_user_when_email_is_valid

---

# Code Review Standards

Reviewers must validate:
- readability
- architecture compliance
- naming consistency
- test coverage
- unnecessary complexity

---

# Formatting

Tools:
- ESLint
- Prettier

Rules:
- formatting automated
- lint errors block merge

---

# Documentation

Required for:
- public APIs
- complex business rules
- architecture decisions

Preferred:
self-documenting code