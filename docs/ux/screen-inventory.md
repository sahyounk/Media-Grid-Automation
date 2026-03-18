# Screen Inventory
## Media Grid Automation Platform

---

## 1. Purpose

This document defines the primary screens for the Media Grid Automation platform, their purpose, the user roles that can access them, the key actions supported on each screen, and the main data elements displayed.

It is intended to guide:
- UX design
- front-end development
- role-based access planning
- navigation and information architecture

---

## 2. Design Principles for Screens

The platform should:
- feel easier than Excel
- support quick planning and editing
- make strategy linkage visible but not heavy
- allow multiple views over the same activity data
- support both operational users and executive viewers
- be white-label friendly
- be localization-ready for English and Arabic

---

## 3. Primary User Roles

- Platform Admin
- Entity Admin
- Strategy Owner
- Planner / Editor
- Approver
- Requester
- Executive / Viewer

---

## 4. Screen Inventory Overview

| Screen ID | Screen Name | Primary Purpose | Main Roles |
|------|------|------|------|
| SCR-01 | Login / Authentication | Sign in and access the platform | All |
| SCR-02 | Landing Dashboard | View summary of activity, approvals, and priorities | Planner, Approver, Executive, Admin |
| SCR-03 | Strategy Library | Manage strategies, pillars, objectives, themes | Strategy Owner, Admin |
| SCR-04 | Strategy Detail | View and edit one strategy and its structure | Strategy Owner, Admin |
| SCR-05 | Activity Grid View | Plan and manage communications activities | Planner, Admin |
| SCR-06 | Activity Calendar View | View activities by date in calendar form | Planner, Executive, Admin |
| SCR-07 | Activity List View | Search, filter, and bulk manage activities | Planner, Admin |
| SCR-08 | Activity Detail Drawer / Page | Create, view, and edit a single activity | Planner, Approver, Admin |
| SCR-09 | Campaign List | View and manage campaigns | Planner, Admin |
| SCR-10 | Campaign Detail | Manage a campaign and linked activities | Planner, Admin |
| SCR-11 | Event List | View and manage events | Planner, Admin |
| SCR-12 | Event Detail | Manage one event and its linked activities | Planner, Admin |
| SCR-13 | Request Intake Form | Submit ad hoc communications requests | Requester |
| SCR-14 | Request Inbox / Triage | Review and convert incoming requests | Planner, Admin |
| SCR-15 | Approval Queue | Review activities awaiting approval | Approver, Admin |
| SCR-16 | Reporting Dashboard | See strategy alignment and activity metrics | Executive, Planner, Admin |
| SCR-17 | Branding & Settings | Manage white-label and entity settings | Entity Admin, Platform Admin |
| SCR-18 | Users & Roles | Manage users, teams, and permissions | Entity Admin, Platform Admin |
| SCR-19 | Taxonomy Management | Manage channels, audiences, tags, categories | Entity Admin, Strategy Owner |
| SCR-20 | Notifications / Alerts | View platform notifications and reminders | All |

---

## 5. Screen Definitions

---

## SCR-01 — Login / Authentication

### Purpose
Authenticate users and route them into the platform securely.

### Main Roles
- All users

### Key Actions
- sign in
- SSO login
- password reset
- session renewal

### Main Data
- email / username
- password or SSO context
- organization branding

---

## SCR-02 — Landing Dashboard

### Purpose
Provide a quick summary of what matters today or this week.

### Main Roles
- Planner / Editor
- Approver
- Executive / Viewer
- Entity Admin

### Key Actions
- view upcoming activities
- view pending approvals
- jump to requests, campaigns, events
- filter by team or date range

### Main Widgets / Data
- upcoming activities
- pending approvals count
- active campaigns
- active events
- recent ad hoc requests
- strategy coverage summary
- quick links to create activity or event

---

## SCR-03 — Strategy Library

### Purpose
Show all strategies available to the organization.

### Main Roles
- Strategy Owner
- Entity Admin

### Key Actions
- create strategy
- view strategies by year/status
- archive strategy
- duplicate strategy structure

### Main Data
- strategy title
- year
- status
- owner
- number of pillars/objectives/themes

---

## SCR-04 — Strategy Detail

### Purpose
Define and manage one strategy and its structure.

### Main Roles
- Strategy Owner
- Entity Admin

### Key Actions
- edit strategy metadata
- add/edit/delete pillars
- add/edit/delete objectives
- add/edit/delete themes
- link supporting notes or attachments

### Main Data
- strategy title and year
- pillars
- objectives
- themes
- optional narratives, audiences, KPIs

---

## SCR-05 — Activity Grid View

### Purpose
Provide the spreadsheet replacement experience for communication planning.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- create new activity
- edit activity inline or via detail view
- drag/drop or reschedule
- filter by team, theme, channel, owner, date
- save view preferences

### Main Data
- title
- date/week/month placement
- owner
- status
- channel
- theme
- campaign/event association
- priority

### Notes
This should be one of the core screens and must be highly usable.

---

## SCR-06 — Activity Calendar View

### Purpose
View planned activities in calendar format.

### Main Roles
- Planner / Editor
- Executive / Viewer
- Entity Admin

### Key Actions
- switch between month/week/day where needed
- click activity to open details
- filter by type, channel, theme, owner
- view key event dates

### Main Data
- scheduled activities by date
- campaigns/events overlaid where relevant

---

## SCR-07 — Activity List View

### Purpose
Provide a searchable and bulk-manageable tabular view of activities.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- search
- advanced filtering
- bulk update
- export results
- sort by priority/date/status

### Main Data
- activity summary rows
- filter values
- bulk action controls

---

## SCR-08 — Activity Detail Drawer / Page

### Purpose
Create, view, and edit a single communications activity.

### Main Roles
- Planner / Editor
- Approver
- Entity Admin

### Key Actions
- create/edit activity
- link to strategy objectives/themes
- assign owner
- attach files
- add comments
- submit for approval
- update workflow status

### Main Data
- title
- description
- activity type
- dates
- owner
- campaign/event links
- strategy links
- channels
- comments
- approval history
- attachments

---

## SCR-09 — Campaign List

### Purpose
View and manage all campaigns.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- create campaign
- filter campaigns
- open campaign detail
- archive or close campaign

### Main Data
- title
- start/end dates
- owner
- status
- linked activity count

---

## SCR-10 — Campaign Detail

### Purpose
Manage one campaign and its related activities.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- edit campaign
- create activities within campaign
- view timeline
- check coverage and status
- add notes

### Main Data
- campaign metadata
- linked activities
- timeline
- owner/status

---

## SCR-11 — Event List

### Purpose
View and manage all events affecting communications planning.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- create event
- filter by event type or date
- open event detail
- archive/cancel event

### Main Data
- title
- event type
- dates
- location
- owner
- linked activity count

---

## SCR-12 — Event Detail

### Purpose
Manage one event and all associated communications activity.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- edit event
- add linked activities
- organize pre-event/live/post-event work
- review communications coverage

### Main Data
- event metadata
- related activities
- associated campaign/theme
- owner/status

---

## SCR-13 — Request Intake Form

### Purpose
Allow internal stakeholders to submit ad hoc communications requests.

### Main Roles
- Requester

### Key Actions
- submit request
- attach reference files
- select urgency and deadline
- optionally reference campaign/theme

### Main Data
- request title
- description
- requester information
- urgency
- deadline
- attachment(s)

---

## SCR-14 — Request Inbox / Triage

### Purpose
Allow communications planners to review and process ad hoc requests.

### Main Roles
- Planner / Editor
- Entity Admin

### Key Actions
- view request queue
- prioritize requests
- convert request to activity
- convert request to campaign
- reject or return request for clarification

### Main Data
- incoming request list
- urgency
- deadline
- requester
- conversion status

---

## SCR-15 — Approval Queue

### Purpose
Allow approvers to review items awaiting approval.

### Main Roles
- Approver
- Entity Admin

### Key Actions
- open activity
- approve
- reject
- comment
- filter by owner/team/type

### Main Data
- activity awaiting approval
- stage name
- requester/planner
- due date
- approval notes

---

## SCR-16 — Reporting Dashboard

### Purpose
Provide executive and planner reporting views.

### Main Roles
- Executive / Viewer
- Planner / Editor
- Entity Admin

### Key Actions
- filter reports
- change time range
- export summaries
- drill into themes/channels/status

### Main Data
- activities by status
- activities by theme
- strategy alignment %
- ad hoc vs planned ratio
- campaign load
- approval backlog
- upcoming key dates

---

## SCR-17 — Branding & Settings

### Purpose
Manage entity-level branding and configuration.

### Main Roles
- Entity Admin
- Platform Admin

### Key Actions
- upload logo
- set colors
- configure terminology
- manage localization defaults
- set entity preferences

### Main Data
- logo
- color palette
- display name
- labels/terminology
- locale/timezone defaults

---

## SCR-18 — Users & Roles

### Purpose
Manage users, teams, and permission access.

### Main Roles
- Entity Admin
- Platform Admin

### Key Actions
- invite users
- edit users
- deactivate users
- assign roles
- assign teams/departments

### Main Data
- user list
- role
- team
- status
- last login (future enhancement)

---

## SCR-19 — Taxonomy Management

### Purpose
Manage reusable controlled values across the platform.

### Main Roles
- Entity Admin
- Strategy Owner

### Key Actions
- manage channels
- manage audiences
- manage tags
- manage activity types
- activate/deactivate taxonomy items

### Main Data
- taxonomy category
- value name
- status
- sort order

---

## SCR-20 — Notifications / Alerts

### Purpose
Show system notifications, reminders, and action prompts.

### Main Roles
- All users

### Key Actions
- view notification
- mark as read
- jump to referenced item

### Main Data
- notification title
- type
- target record
- timestamp
- read/unread state

---

## 6. Navigation Recommendations

Primary navigation should likely include:
- Dashboard
- Activities
- Campaigns
- Events
- Requests
- Strategy
- Reporting
- Admin

Navigation should adapt by role so non-admin users are not overloaded.

---

## 7. MVP Screen Recommendation

For MVP, prioritize these screens first:

1. SCR-01 Login / Authentication
2. SCR-02 Landing Dashboard
3. SCR-04 Strategy Detail
4. SCR-05 Activity Grid View
5. SCR-08 Activity Detail
6. SCR-11 Event List
7. SCR-12 Event Detail
8. SCR-13 Request Intake Form
9. SCR-14 Request Inbox / Triage
10. SCR-15 Approval Queue
11. SCR-16 Reporting Dashboard
12. SCR-17 Branding & Settings

---

## 8. Future Screen Enhancements

Later versions may add:
- AI suggestion panel
- strategy upload/parsing wizard
- playbook generator wizard
- executive weekly briefing screen
- calendar sync settings
- audit log viewer
- cross-entity portfolio dashboard for platform admins

---

## 9. Notes for Design and Development

- Activity Grid View and Activity Detail are the most critical UX investments
- Strategy tagging must be easy and fast
- Request Intake must feel simple for non-comms users
- Reporting must work for both operational and executive audiences
- White-label settings should not complicate the core planning workflow

---

End of Document
