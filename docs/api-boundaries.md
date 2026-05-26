# Loom API Boundaries

This document defines the API boundaries for Loom.

---

# API Strategy

Loom is API-first.

Priority:
Contracts
→ API
→ Frontend

All APIs must be contract-driven.

---

# Public API

Purpose:
Expose Loom functionality to external consumers.

Transport:
REST

Base path:
/api/v1

Examples:
GET /api/v1/content
POST /api/v1/content
GET /api/v1/media

Authentication:
JWT Bearer

---

# Future API Support

Planned:
- GraphQL
- Webhooks

Not MVP

---

# Internal Module Communication

Modules communicate through:

Application Services

Example:
ContentService calls MediaService via interface

Allowed:
service-to-service

Forbidden:
direct database access between modules

---

# Event Communication

Future asynchronous communication:

Examples:
- ContentPublished
- UserCreated
- MediaUploaded

Pattern:
Domain Events

Not required in MVP

---

# API Versioning

Strategy:
URI versioning

Example:
/api/v1
/api/v2

Rules:
- breaking changes require new version
- non-breaking changes stay in same version

---

# DTO Ownership

DTOs live in:

@loom/contracts

Rules:
- backend owns contracts
- frontend consumes contracts
- contracts are shared

---

# Validation Rules

Validation occurs:
- at API boundary
- before application layer

Tools:
class-validator / zod (decision later)

---

# Error Strategy

Standard response:

{
  "code": "CONTENT_NOT_FOUND",
  "message": "Content not found"
}

Rules:
- predictable
- typed
- documented

---

# Security Boundary

Required:
- authentication
- authorization
- input validation
- rate limiting (future)