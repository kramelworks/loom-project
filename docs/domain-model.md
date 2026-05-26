# Loom Domain Model

This document defines the initial domain model for Loom.

---

# Bounded Contexts

Loom is divided into the following bounded contexts:

- Identity
- Access Control
- Content Modeling
- Content Management
- Media Management
- Administration

---

# Core Entities

## User

Represents a platform user.

Attributes:
- id
- name
- email
- passwordHash
- status
- createdAt

Relationships:
- has many Roles

---

## Role

Represents a group of permissions.

Attributes:
- id
- name
- description

Relationships:
- has many Permissions
- has many Users

---

## Permission

Represents a system capability.

Examples:
- content.read
- content.write
- media.upload

---

## ContentType

Defines a content schema.

Attributes:
- id
- name
- slug
- fields

Relationships:
- has many ContentEntries

Aggregate Root:
Yes

---

## ContentEntry

Represents a content instance.

Attributes:
- id
- title
- slug
- status
- data
- publishedAt

Relationships:
- belongs to ContentType

---

## MediaAsset

Represents uploaded media.

Attributes:
- id
- filename
- mimeType
- size
- url

Relationships:
- optional owner User

---

## Workspace (future)

Supports multi-tenancy.

Attributes:
- id
- name

Relationships:
- owns users
- owns content

MVP:
No

---

# Aggregate Roots

Defined roots:

- User
- Role
- ContentType
- ContentEntry
- MediaAsset

---

# Entity Relationships

User -> Role (many-to-many)

Role -> Permission (many-to-many)

ContentType -> ContentEntry (one-to-many)

User -> MediaAsset (one-to-many)

---

# Domain Rules

- Users must have unique email
- ContentType names must be unique
- ContentEntry slug must be unique
- Roles must not duplicate permissions
- Media must validate file type

---

# Future Extensions

- versioning
- localization
- workflows
- webhooks