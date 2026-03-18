# API Specification v1
## Media Grid Automation Platform

---

## 1. Purpose

This document defines the REST API surface for version 1 of the Media Grid Automation platform.

The API is designed to support:
- front-end web application functionality
- white-label multi-entity support
- strategy-aligned communications planning
- activity, campaign, event, and request management
- workflow, approvals, and reporting

---

## 2. API Design Principles

- REST-based, resource-oriented design
- JSON request and response bodies
- versioned endpoint prefix
- secure, authenticated access
- role-based authorization
- filterable list endpoints
- consistent error handling
- support for pagination where needed

---

## 3. Base URL

    /api/v1

---

## 4. Authentication Model

All protected endpoints require authentication.

### Supported authentication methods
- session/cookie auth for web app deployments
- bearer token auth for API clients and integrations
- SSO-backed authentication in enterprise deployments

### Example header

    Authorization: Bearer <token>

---

## 5. Standard Response Patterns

### 5.1 Success Response

    {
      "success": true,
      "data": {}
    }

### 5.2 Error Response

    {
      "success": false,
      "error": {
        "code": "VALIDATION_ERROR",
        "message": "One or more fields are invalid.",
        "details": []
      }
    }

### 5.3 Paginated Response

    {
      "success": true,
      "data": [],
      "meta": {
        "page": 1,
        "page_size": 25,
        "total_items": 240,
        "total_pages": 10
      }
    }

---

## 6. Common Query Parameters

| Parameter | Type | Purpose |
|------|------|---------|
| page | integer | Page number |
| page_size | integer | Number of results per page |
| search | string | Full-text search |
| sort_by | string | Sort field |
| sort_order | string | asc or desc |
| status | string | Filter by status |
| start_date | date | Filter from date |
| end_date | date | Filter to date |

---
## 7. Auth Endpoints

### 7.1 Get Current User
**GET** `/auth/me`

#### Response

    {
      "success": true,
      "data": {
        "id": "uuid",
        "first_name": "Karim",
        "last_name": "Sahyoun",
        "email": "user@example.com",
        "role": "entity_admin",
        "organization_id": "uuid"
      }
    }

### 7.2 Logout
**POST** `/auth/logout`

#### Response

    {
      "success": true,
      "data": {
        "message": "Logged out successfully."
      }
    }

---

## 8. Organization Endpoints

### 8.1 Get Organization
**GET** `/organizations/{organizationId}`

### 8.2 Update Organization
**PATCH** `/organizations/{organizationId}`

#### Request Body

    {
      "name": "Generic Government Entity",
      "timezone": "Asia/Dubai",
      "default_language": "en"
    }

---

## 9. Strategy Endpoints

### 9.1 List Strategies
**GET** `/strategies`

#### Optional Filters
- status
- year

### 9.2 Create Strategy
**POST** `/strategies`

#### Request Body

    {
      "title": "2026 Communications Strategy",
      "year": 2026,
      "status": "draft"
    }

### 9.3 Get Strategy
**GET** `/strategies/{strategyId}`

### 9.4 Update Strategy
**PATCH** `/strategies/{strategyId}`

### 9.5 Delete Strategy
**DELETE** `/strategies/{strategyId}`

---

## 10. Strategy Pillar Endpoints

### 10.1 Create Pillar
**POST** `/strategies/{strategyId}/pillars`

#### Request Body

    {
      "name": "Public Engagement",
      "description": "Increase public awareness and participation."
    }

### 10.2 Update Pillar
**PATCH** `/pillars/{pillarId}`

### 10.3 Delete Pillar
**DELETE** `/pillars/{pillarId}`

---

## 11. Objective Endpoints

### 11.1 Create Objective
**POST** `/pillars/{pillarId}/objectives`

#### Request Body

    {
      "name": "Promote preventive healthcare awareness",
      "description": "Support education and outreach through campaigns and events."
    }

### 11.2 Update Objective
**PATCH** `/objectives/{objectiveId}`

### 11.3 Delete Objective
**DELETE** `/objectives/{objectiveId}`

---

## 12. Theme Endpoints

### 12.1 List Themes
**GET** `/themes`

### 12.2 Create Theme
**POST** `/themes`

#### Request Body

    {
      "strategy_id": "uuid",
      "name": "Women's Health Week",
      "start_date": "2026-03-01",
      "end_date": "2026-03-07"
    }

### 12.3 Update Theme
**PATCH** `/themes/{themeId}`

### 12.4 Delete Theme
**DELETE** `/themes/{themeId}`

---
## 13. Campaign Endpoints

### 13.1 List Campaigns
**GET** `/campaigns`

### 13.2 Create Campaign
**POST** `/campaigns`

#### Request Body

    {
      "title": "Women's Health Awareness Campaign",
      "start_date": "2026-03-01",
      "end_date": "2026-03-31",
      "owner_id": "uuid"
    }

### 13.3 Get Campaign
**GET** `/campaigns/{campaignId}`

### 13.4 Update Campaign
**PATCH** `/campaigns/{campaignId}`

### 13.5 Delete Campaign
**DELETE** `/campaigns/{campaignId}`

### 13.6 List Campaign Activities
**GET** `/campaigns/{campaignId}/activities`

---

## 14. Event Endpoints

### 14.1 List Events
**GET** `/events`

### 14.2 Create Event
**POST** `/events`

#### Request Body

    {
      "title": "World Government Summit",
      "event_type": "conference",
      "start_date": "2026-02-10",
      "end_date": "2026-02-12"
    }

### 14.3 Get Event
**GET** `/events/{eventId}`

### 14.4 Update Event
**PATCH** `/events/{eventId}`

### 14.5 Delete Event
**DELETE** `/events/{eventId}`

### 14.6 List Event Activities
**GET** `/events/{eventId}/activities`

---

## 15. Activity Endpoints

### 15.1 List Activities
**GET** `/activities`

#### Optional Filters
- status
- owner_id
- campaign_id
- event_id
- objective_id
- theme_id
- channel_id
- activity_type
- planned_date
- start_date
- end_date
- priority

### 15.2 Create Activity
**POST** `/activities`

#### Request Body

    {
      "title": "Minister interview on women's health",
      "description": "Coordinate TV interview aligned to Women's Health Week.",
      "activity_type": "interview",
      "status": "draft",
      "priority": "high",
      "owner_id": "uuid",
      "planned_date": "2026-03-03",
      "campaign_id": "uuid",
      "event_id": null,
      "objective_ids": ["uuid"],
      "theme_ids": ["uuid"],
      "channel_ids": ["uuid"]
    }

### 15.3 Get Activity
**GET** `/activities/{activityId}`

### 15.4 Update Activity
**PATCH** `/activities/{activityId}`

### 15.5 Delete Activity
**DELETE** `/activities/{activityId}`

### 15.6 Bulk Update Activities
**POST** `/activities/bulk-update`

#### Request Body

    {
      "activity_ids": ["uuid", "uuid"],
      "changes": {
        "status": "approved",
        "owner_id": "uuid"
      }
    }

### 15.7 Link Activity to Objectives
**POST** `/activities/{activityId}/objectives`

#### Request Body

    {
      "objective_ids": ["uuid", "uuid"]
    }

### 15.8 Link Activity to Themes
**POST** `/activities/{activityId}/themes`

#### Request Body

    {
      "theme_ids": ["uuid"]
    }

### 15.9 Link Activity to Channels
**POST** `/activities/{activityId}/channels`

#### Request Body

    {
      "channel_ids": ["uuid", "uuid"]
    }

---
## 16. Request Intake Endpoints

### 16.1 List Requests
**GET** `/requests`

#### Optional Filters
- status
- urgency
- requester_department
- requested_deadline

### 16.2 Submit Request
**POST** `/requests`

#### Request Body

    {
      "title": "Support media coverage for local summit",
      "description": "Need social posts, press release, and spokesperson support.",
      "requester_name": "Department Lead",
      "urgency": "high",
      "requested_deadline": "2026-02-15"
    }

### 16.3 Get Request
**GET** `/requests/{requestId}`

### 16.4 Update Request
**PATCH** `/requests/{requestId}`

### 16.5 Convert Request to Activity
**POST** `/requests/{requestId}/convert-to-activity`

#### Request Body

    {
      "owner_id": "uuid",
      "status": "draft"
    }

### 16.6 Convert Request to Campaign
**POST** `/requests/{requestId}/convert-to-campaign`

---

## 17. Approval Endpoints

### 17.1 List Approvals
**GET** `/approvals`

#### Optional Filters
- decision
- approver_id
- activity_id

### 17.2 Submit Activity for Approval
**POST** `/activities/{activityId}/submit-for-approval`

#### Request Body

    {
      "approver_id": "uuid",
      "stage_name": "content_review"
    }

### 17.3 Approve Activity
**POST** `/activities/{activityId}/approve`

#### Request Body

    {
      "comments": "Approved for scheduling."
    }

### 17.4 Reject Activity
**POST** `/activities/{activityId}/reject`

#### Request Body

    {
      "comments": "Please revise message framing."
    }

---

## 18. Comment Endpoints

### 18.1 List Comments for Activity
**GET** `/activities/{activityId}/comments`

### 18.2 Add Comment to Activity
**POST** `/activities/{activityId}/comments`

#### Request Body

    {
      "body": "Please confirm spokesperson availability."
    }

---

## 19. Attachment Endpoints

### 19.1 Upload Attachment to Activity
**POST** `/activities/{activityId}/attachments`

#### Request
Multipart form-data upload

### 19.2 List Activity Attachments
**GET** `/activities/{activityId}/attachments`

### 19.3 Delete Attachment
**DELETE** `/attachments/{attachmentId}`

---

## 20. Reporting Endpoints

### 20.1 Dashboard Summary
**GET** `/reporting/dashboard-summary`

#### Response Example

    {
      "success": true,
      "data": {
        "upcoming_activities": 42,
        "pending_approvals": 7,
        "active_campaigns": 5,
        "active_events": 3
      }
    }

### 20.2 Strategy Alignment Report
**GET** `/reporting/strategy-alignment`

#### Response Example

    {
      "success": true,
      "data": {
        "linked_activities_percentage": 82,
        "unlinked_activities_count": 11,
        "activities_by_theme": [
          {
            "theme": "Women's Health Week",
            "count": 14
          }
        ]
      }
    }

### 20.3 Activity Breakdown Report
**GET** `/reporting/activity-breakdown`

#### Optional Filters
- by=status
- by=channel
- by=activity_type
- by=owner
- by=theme

### 20.4 Export Activities
**GET** `/reporting/export/activities`

#### Supported Formats
- csv
- xlsx
- pdf

---

## 21. Settings and White-Label Endpoints

### 21.1 Get Branding Settings
**GET** `/settings/branding`

### 21.2 Update Branding Settings
**PATCH** `/settings/branding`

#### Request Body

    {
      "logo_url": "https://example.com/logo.png",
      "primary_color": "#0055AA",
      "entity_display_name": "Generic Public Entity"
    }

### 21.3 Get Terminology Settings
**GET** `/settings/terminology`

### 21.4 Update Terminology Settings
**PATCH** `/settings/terminology`

---

## 22. Role and Permission Considerations

The API must enforce permissions such as:
- view_strategy
- edit_strategy
- create_activity
- edit_activity
- approve_activity
- manage_requests
- view_reporting
- manage_branding
- manage_users

Authorization must be checked server-side on every protected endpoint.

---

## 23. Validation Rules

Examples:
- required fields must be present on create
- dates must be valid ISO dates
- end_date must not be before start_date
- referenced IDs must belong to the same organization/tenant where applicable
- invalid workflow transitions must be rejected
- deleted or inactive linked objects must not be attached unless explicitly allowed

---

## 24. Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 422 | Validation Error |
| 500 | Internal Server Error |

---

## 25. Future API Extensions

Planned for later phases:
- AI suggestion endpoints
- strategy document upload and parsing
- playbook generation endpoints
- external publishing integrations
- notification preferences APIs
- audit log retrieval APIs
- calendar sync APIs

---

## 26. Recommended Next API Documents

After this file, split out the detailed per-domain specs into:
- auth-api.md
- strategy-api.md
- activity-api.md
- campaign-api.md
- event-api.md
- request-api.md
- workflow-api.md
- reporting-api.md

---

End of Document
