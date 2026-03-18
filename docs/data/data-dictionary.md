# Data Dictionary
## Media Grid Automation Platform

---

## 1. Purpose

This document defines all core data entities, fields, relationships, and constraints for the platform.

It serves as the **source of truth for database design and API contracts**.

---

## 2. Core Design Principles

- all entities use UUIDs
- all tables include created_at and updated_at
- relationships are explicit
- many-to-many relationships use join tables
- fields are designed for filtering and reporting
- auditability is preserved

---

## 3. Core Entities Overview

- Tenant
- Organization
- User
- Role
- Strategy
- StrategyPillar
- Objective
- Theme
- Audience
- Channel
- Campaign
- Event
- Activity
- Request
- Approval
- Comment
- Attachment

---

## 4. Entity Definitions

---

## 4.1 Tenant

| Field | Type | Required | Description |
|------|------|----------|------------|
| id | UUID | Yes | Unique tenant ID |
| name | String | Yes | Tenant name |
| slug | String | Yes | URL identifier |
| created_at | Timestamp | Yes | Creation time |
| updated_at | Timestamp | Yes | Last update |

---

## 4.2 Organization

| Field | Type | Required | Description |
|------|------|----------|------------|
| id | UUID | Yes |
| tenant_id | UUID | Yes |
| name | String | Yes |
| country | String | No |
| timezone | String | Yes |
| default_language | String | Yes |
| created_at | Timestamp | Yes |
| updated_at | Timestamp | Yes |

---

## 4.3 User

| Field | Type | Required | Description |
|------|------|----------|------------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| first_name | String | Yes |
| last_name | String | Yes |
| email | String | Yes |
| role | String | Yes |
| status | String | Yes |
| created_at | Timestamp | Yes |
| updated_at | Timestamp | Yes |

---

## 4.4 Strategy

| Field | Type | Required | Description |
|------|------|----------|------------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| title | String | Yes |
| year | Integer | Yes |
| status | String | Yes |
| created_at | Timestamp | Yes |
| updated_at | Timestamp | Yes |

---

## 4.5 Strategy Pillar

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| strategy_id | UUID | Yes |
| name | String | Yes |
| description | Text | No |

---

## 4.6 Objective

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| strategy_id | UUID | Yes |
| pillar_id | UUID | Yes |
| name | String | Yes |
| description | Text | No |

---

## 4.7 Theme

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| strategy_id | UUID | Yes |
| name | String | Yes |
| start_date | Date | No |
| end_date | Date | No |

---

## 4.8 Campaign

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| title | String | Yes |
| start_date | Date | No |
| end_date | Date | No |
| owner_id | UUID | Yes |

---

## 4.9 Event

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| title | String | Yes |
| event_type | String | Yes |
| start_date | Date | Yes |
| end_date | Date | Yes |

---

## 4.10 Activity (MOST IMPORTANT)

| Field | Type | Required | Description |
|------|------|----------|------------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| title | String | Yes |
| description | Text | No |
| activity_type | String | Yes |
| status | String | Yes |
| priority | String | No |
| owner_id | UUID | Yes |
| planned_date | Date | Yes |
| start_date | Date | No |
| end_date | Date | No |
| campaign_id | UUID | No |
| event_id | UUID | No |
| created_at | Timestamp | Yes |
| updated_at | Timestamp | Yes |

---

## 4.11 Activity Relationships

### Activity → Strategy Objectives

| Field | Type |
|------|------|
| activity_id | UUID |
| objective_id | UUID |

### Activity → Themes

| Field | Type |
|------|------|
| activity_id | UUID |
| theme_id | UUID |

### Activity → Channels

| Field | Type |
|------|------|
| activity_id | UUID |
| channel_id | UUID |

---

## 4.12 Request

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| organization_id | UUID | Yes |
| title | String | Yes |
| description | Text | Yes |
| requester_name | String | Yes |
| urgency | String | Yes |
| requested_deadline | Date | Yes |
| status | String | Yes |

---

## 4.13 Approval

| Field | Type | Required |
|------|------|----------|
| id | UUID | Yes |
| activity_id | UUID | Yes |
| approver_id | UUID | Yes |
| decision | String | Yes |
| decision_date | Timestamp | No |

---

## 5. Key Relationships Summary

- Organization → Users (1:N)
- Strategy → Pillars → Objectives (1:N:N)
- Activity → Strategy (many-to-many)
- Activity → Campaign (N:1)
- Activity → Event (N:1)
- Activity → Channels (many-to-many)
- Request → Activity (optional conversion)

---

## 6. Notes

- Activity is the central entity
- Everything connects to Activity
- Strategy linkage is critical for reporting
- Flexibility is required for different entity structures

---

End of Document
