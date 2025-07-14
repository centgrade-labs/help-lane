# 🧩 Internal Support Ticket System – Design Specification

This document outlines the design structure, user interface layout, component behavior, and interactions for the internal support ticket system.

---

## 🎯 Design Goals

- Clean, minimalistic UI with high usability
- Responsive layout with consistent UX across roles
- Easy ticket creation and collaboration
- Admin interface for managing categories, statuses, priorities
- Works well with Tailwind CSS and shadcn/ui components

---

## 📱 Layout System

### Global Layout
- **Sidebar Navigation** (left)
- **Header Bar** (top): user avatar, name, logout
- **Main Content Area**: scrollable with padding
- **Modals**: ticket creation, edit forms, confirmations
- **Toasts**: for success/error messages

---

## 🎨 Color Palette

| Purpose             | Color                |
|---------------------|----------------------|
| Primary             | `#3B82F6` (blue-500) |
| Secondary           | `#F59E0B` (amber-500)|
| Success             | `#10B981` (green-500)|
| Error               | `#EF4444` (red-500)  |
| Background          | `#F9FAFB` (gray-50)  |
| Border              | `#E5E7EB` (gray-200) |

Use Tailwind utility classes and semantic color naming.

---

## 🧭 Sidebar Navigation

### For All Users:
- 🏠 Dashboard
- ➕ Create Ticket
- 📄 My Tickets
- 📥 Assigned to My Team

### For Admins:
- 🧾 All Tickets
- 👥 Manage Users
- 👨‍👩‍👧‍👦 Manage Teams
- 🧱 Ticket Categories
- 🎯 Ticket Priorities
- 🚦 Ticket Statuses
- 📈 Reports

---

## 🧱 Pages & Components

### 1. Dashboard
- Metric cards: Open, In Progress, Resolved
- Recent Tickets Table
- Quick Filters: My Tickets, Team Tickets

### 2. Create Ticket Modal
- Team (select)
- Category (select)
- Priority (select)
- Description (textarea)
- File Upload (drag/drop or file picker)
- External User Identifier (text input)
- Identifier Type (select: `mobile`, `email`)

### 3. Ticket List View
- Table with:
  - Ticket ID
  - Created by (Employee)
  - Status (colored tag)
  - Priority (colored tag)
  - Assigned Team
  - Category
  - External User (if any)
  - Actions: View, Edit, Assign

### 4. Ticket Detail View
- Ticket Info (top section)
- Status, Priority, Assigned Team editable in-place
- External user reference (display-only)
- Timeline of activity
- **Chat section:**
  - Messages shown in vertical order
  - Message sender, timestamp, file attachments
  - Input bar with message box + file upload

### 5. Manage Categories / Statuses / Priorities
- Table of records with add/edit/delete buttons
- Use modal forms
- Toggle for active/inactive (in categories)

---

## 🧩 UI Components

- `Button`: primary, secondary, ghost
- `Input`: text, textarea, select, file
- `Card`: dashboard metrics
- `Table`: lists with sorting + filtering
- `Badge`: for status/priority labels
- `Modal`: for create/edit forms
- `Avatar`: employee initials/photo

Use [shadcn/ui](https://ui.shadcn.com/docs/components) wherever possible.

---

## 🔁 Interactions

- Modal close on outside click or ESC
- Form validation before submission
- Toast on success/failure
- Poll chat messages every 15 seconds (simple HTTP polling)
- Optional confirmation dialog for closing/deleting tickets

---

## ✅ Accessibility Considerations

- Use semantic HTML for form inputs and tables
- Proper focus states and keyboard navigation
- All buttons must have accessible labels

---

## 📱 Responsive Behavior

- Sidebar collapses to icon-only version on small screens
- Tables become stacked cards on mobile
- Modal dialogs full-width on small screens

---

## ✨ Optional Enhancements

- Dark mode toggle
- Saved filters
- CSV export for admins
- Activity timeline on tickets (status/priority/category changes)
