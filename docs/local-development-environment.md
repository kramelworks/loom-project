# Loom Local Development Environment

This document defines the local development environment for Loom.

---

# Goals

The local environment must be:
- simple
- reproducible
- beginner-friendly
- cross-platform

Supported OS:
- Windows
- Linux
- macOS

---

# Required Tools

## Core Tools

Required:
- Git
- Node.js
- npm

Preferred versions:
- Node.js LTS
- npm latest stable

---

# Recommended IDE

IDE:
VS Code

Recommended extensions:
- ESLint
- Prettier
- Prisma
- Tailwind CSS IntelliSense
- GitLens

---

# Repository Setup

Example:

git clone <repo>
cd loom-api
npm install

---

# Environment Variables

Strategy:
.env files

Rules:
- never commit secrets
- use .env.example
- environment-specific variables

Examples:
.env
.env.development
.env.test

---

# Backend Local Setup

Repository:
loom-api

Steps:

1. install dependencies
2. configure .env
3. initialize database
4. run migrations
5. start server

Commands:

npm install
npm run db:migrate
npm run dev

---

# Frontend Local Setup

Repository:
loom-web

Steps:

1. install dependencies
2. configure .env
3. start frontend

Commands:

npm install
npm run dev

---

# Database Strategy

Development database:
SQLite

Reason:
- lightweight
- zero setup
- beginner friendly

Production:
Azure SQL

---

# ORM

ORM:
Prisma

Commands:

npm run prisma:generate
npm run prisma:migrate

---

# Ports

Default ports:

Backend:
3000

Frontend:
3001

Rules:
- avoid conflicts
- document custom ports

---

# Authentication Setup

Initial strategy:
local JWT authentication

No external providers required for local setup.

---

# Shared Packages Development

Local linking strategy:
npm workspaces or npm link (decision later)

Rules:
- shared packages tested independently
- avoid hidden local dependencies

---

# Git Workflow

Developer flow:

1. create branch
2. implement changes
3. run tests
4. create PR

Branch naming:
feature/*
bugfix/*
hotfix/*

---

# Quality Checks Before PR

Required:
- lint passing
- tests passing
- build passing

Commands:

npm run lint
npm run test
npm run build

---

# Troubleshooting

Common issues:
- Node version mismatch
- locked SQLite file
- missing .env variables

Rules:
- document recurring issues
- improve onboarding continuously

---

# Future Improvements

Possible future additions:
- Docker setup
- Dev Containers
- automated environment bootstrap
- seeded development database