# Loom Frontend Project Structure

This document defines the frontend structure for Loom.

Repository:
loom-web

Stack:
- Next.js
- TypeScript

Architecture:
- Feature-first
- Component-driven
- API-first

---

# High-Level Structure

src/
├── app/
├── features/
├── components/
├── services/
├── hooks/
├── providers/
├── layouts/
├── styles/
├── shared/
└── tests/

---

# App Router

Loom uses:
Next.js App Router

Structure:

src/app/
├── login/
├── dashboard/
├── content/
└── settings/

Rules:
- route-only logic
- avoid business logic in pages

---

# Features

Purpose:
Business-focused frontend modules.

Example:

src/features/
 └── users/
      ├── components/
      ├── hooks/
      ├── services/
      ├── types/
      └── tests/

Rules:
- isolated by domain
- feature ownership
- reusable internally

---

# Shared Components

Purpose:
Reusable UI components.

Structure:

src/components/
├── ui/
├── forms/
├── feedback/
└── layouts/

Examples:
Button
Modal
Table
Input

Rules:
- presentation-focused
- no business logic

---

# Services Layer

Purpose:
API communication.

Structure:

src/services/
├── api-client.ts
├── auth-service.ts
└── content-service.ts

Rules:
- centralized HTTP client
- typed responses only
- contracts from @loom/contracts

---

# State Management

Initial strategy:
React Query + local state

Rules:
- server state via React Query
- UI state local when possible

Avoid:
global state unless necessary

Future:
Zustand (if needed)

---

# Forms

Preferred:
React Hook Form

Validation:
zod

Rules:
- schema-first validation
- typed forms

---

# Styling

Strategy:
TailwindCSS

Rules:
- utility-first
- avoid inline styles
- avoid duplicated patterns

---

# Shared Folder

Purpose:
Cross-feature reusable logic.

Structure:

src/shared/
├── constants/
├── utils/
├── types/
└── config/

Rules:
- no feature business logic

---

# Hooks

Structure:

src/hooks/
├── use-auth.ts
├── use-theme.ts
└── use-debounce.ts

Rules:
- reusable behavior only
- avoid over-abstraction

---

# Providers

Purpose:
Global app providers.

Examples:
- QueryClientProvider
- ThemeProvider
- AuthProvider

---

# Testing Structure

Structure:

tests/
├── unit/
├── integration/
└── e2e/

Tools:
- Vitest
- Testing Library
- Playwright (future)

---

# Dependency Rules

Allowed:
features
→ shared/components/services

Forbidden:
feature-to-feature direct coupling

---

# API Integration

Backend communication:
REST API

Base URL:
/api/v1

Contracts:
@loom/contracts

---

# Authentication Strategy

Initial:
JWT access token

Future:
refresh token rotation
OAuth providers

---

# Future Evolution

Possible future apps:
- loom-studio
- loom-public-admin
- loom-mobile

Current strategy:
single admin application