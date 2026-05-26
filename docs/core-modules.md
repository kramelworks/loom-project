# Loom Core Modules

This document defines the core modules of Loom.

---

# Product Modules

Loom is organized into modular domains.

Each module owns its own:
- domain
- application logic
- infrastructure
- API contracts

---

# 1. Identity

Purpose:
Authentication and session management.

Responsibilities:
- login
- logout
- token handling
- password reset
- OAuth (future)

MVP:
Yes

---

# 2. Users

Purpose:
User lifecycle management.

Responsibilities:
- create users
- update users
- deactivate users
- profile management

MVP:
Yes

---

# 3. Roles & Permissions

Purpose:
Authorization.

Responsibilities:
- RBAC
- policies
- role assignment

MVP:
Yes

---

# 4. Content Types

Purpose:
Define schemas for content.

Responsibilities:
- create content models
- fields
- validations

MVP:
Yes

---

# 5. Content

Purpose:
Manage content entries.

Responsibilities:
- CRUD
- drafts
- publishing

MVP:
Yes

---

# 6. Media

Purpose:
Media asset management.

Responsibilities:
- upload
- storage
- metadata

MVP:
Yes

---

# 7. API

Purpose:
Expose content externally.

Responsibilities:
- REST endpoints
- future GraphQL support

MVP:
Yes

---

# 8. Admin UI

Purpose:
Backoffice interface.

Responsibilities:
- dashboard
- forms
- content management

MVP:
Yes

---

# 9. Audit

Purpose:
Track important actions.

Responsibilities:
- event logs
- change history

MVP:
No (v0.3)

---

# 10. Notifications

Purpose:
Internal notifications/events.

Responsibilities:
- emails
- webhooks
- event bus

MVP:
No (future)

---

# Module Boundaries

Rules:
- modules do not access each other's database directly
- communication via application services/contracts
- shared code only in shared packages