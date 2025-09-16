# Issue Tracker Project

## 🧾 Project Idea: **Issue Tracker (Bug Reporting System)**

A basic issue tracking system — like a mini GitHub Issues — without the drag-and-drop.

---

### ✅ Core Features

- Users can **create, view, edit, and delete issues**
- Each issue has:
    - Title
    - Description
    - Status: Open | In Progress | Resolved
    - Priority: Low | Medium | High
- Issues are displayed in a **list grouped by status**
- Status can be updated via a dropdown or button

---

### 🖼️ Visual Layout (Main UI – `/issues`)

```Plain
┌─────────────────────────────────────────────┐
│                 🐞 Issue Tracker             │
│─────────────────────────────────────────────│
│ [ + New Issue ]                              │
│                                             │
│ ┌────── Open ──────┐  ┌── In Progress ─┐  ┌── Resolved ──┐
│ │ #45  Login fails │  │ #39  CSS bugs  │  │ #21  Fixed   │
│ │ High priority    │  │ Medium prio.   │  │ Login fixed  │
│ │ [View] [Edit]    │  │ [View] [Edit]  │  │ [View]       │
│ └──────────────────┘  └────────────────┘  └──────────────┘
│                                             │
└─────────────────────────────────────────────┘
```

---

### 🛠 Tech Stack

- **React**
    - State and status filtering
    - Form handling
    - Routing for `/issues`, `/issues/:id`, `/add`, `/edit/:id`
- **Flask**
    - REST API (CRUD operations)
    - SQLite for storage

### 🔄 Backend API Endpoints

|Method|Endpoint|Purpose|
|---|---|---|
|GET|`/issues`|Get all issues|
|GET|`/issues/<id>`|Get single issue|
|POST|`/issues`|Create issue|
|PUT|`/issues/<id>`|Update issue/status|
|DELETE|`/issues/<id>`|Delete issue|

---

### 📝 Example Issue Object

```JSON
{
  "id": 45,
  "title": "Login fails on Safari",
  "description": "User gets stuck on loading screen.",
  "status": "open",
  "priority": "high"
}
```

---

### 🧠 Why It’s Great for You Now

- No drag-and-drop needed
- Clean full-stack architecture (CRUD, routing, list views)
- Helps you work with form validation, filters, and status toggles
- Looks and behaves like a real-world admin-style tool

---
