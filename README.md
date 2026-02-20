# 🏛️ Department Web Portal — Digital Library & Notice Board

A centralized web portal for departments, designed to streamline the flow of academic resources and communications between the **HOD (Admin)**, **Faculty**, and **Students**. Think of it as a smart ERP-style interface combining a digital library, a gatekeeper approval system, and a live notice board.

---

## 📌 Table of Contents

- [Overview](#overview)
- [User Roles](#user-roles)
- [Modules](#modules)
  - [1. Authentication & Security](#1-authentication--security)
  - [2. Smart Repository](#2-smart-repository-upload--download)
  - [3. Gatekeeper Approval System](#3-gatekeeper-approval-system)
  - [4. Advanced Search & Filtering](#4-advanced-search--filtering-engine)
  - [5. Digital Notice Board](#5-digital-notice-board)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

---

## 🧭 Overview

This portal acts as a **department-level knowledge hub** where:

- Faculty can upload and manage academic resources instantly.
- Students can discover, filter, and download materials — as well as contribute their own notes (subject to approval).
- HOD can govern content quality through an approval workflow and broadcast notices to the entire department.

---

## 👥 User Roles

| Role | Description | Key Permissions |
|------|-------------|-----------------|
| 🔴 **Admin (HOD)** | Super User — oversees the entire system | Post notices, approve/reject uploads, manage users |
| 🟡 **Faculty** | Content creators and approvers | Upload resources (live immediately), review student uploads |
| 🟢 **Student** | Consumers and peer contributors | Search/download resources, upload notes (pending approval) |

---

## 📦 Modules

### 1. Authentication & Security

Secure, role-based access control for all users.

- **Student Registration** — Sign up using:
  - USN (University Seat Number)
  - Full Name
  - Semester
- **Login** — Secure login for all three roles (Admin, Faculty, Student).
- **Validation Rules**:
  - No duplicate accounts — one USN can only map to one account.
  - Role-specific dashboards on login.

---

### 2. Smart Repository (Upload & Download)

The **core feature** of the portal. All materials are organized by:

```
Semester → Subject → Unit
```

#### ✅ Supported File Formats

| # | Format | Use Case |
|---|--------|----------|
| 1 | `.pdf` | Documents, Notes |
| 2 | `.ppt` / `.pptx` | Presentations |
| 3 | `.doc` / `.docx` | Assignments |
| 4 | `.jpg` / `.png` | Whiteboard/Handwritten Notes |

#### 📤 Faculty Uploads
- Can upload **Textbooks** (large files), **Reference Links** (URLs), and **Official Notes**.
- All faculty uploads are **published immediately** — no approval required.

#### 📤 Student Uploads
- Students can submit their own notes.
- All student uploads enter a **"Pending Approval"** state and are **not visible** to others until reviewed.

---

### 3. Gatekeeper Approval System

Prevents spam and ensures content quality.

**Workflow:**

```
Student Uploads File
        ↓
  Status: PENDING
        ↓
HOD / Faculty Reviews in "Review Uploads" Tab
        ↓
   ┌────┴────┐
APPROVE     REJECT
   ↓           ↓
PUBLISHED    DELETED
(Visible    (Removed
to all)     from system)
```

- Only files with **Status: Approved** appear in search results.
- Reviewers can **preview** the file before making a decision.

---

### 4. Advanced Search & Filtering Engine

A smart filtering system so students can find materials without endless scrolling.

**Filter Options (Dropdown-based):**

| Filter | Example |
|--------|---------|
| Subject Code | `BCA401` |
| Semester | `4th Sem` |
| Uploaded By (Professor) | `Notes by Prof. Sharma` |

**Output:** A clean **grid view** of all matching approved files.

---

### 5. Digital Notice Board

A dedicated section on the homepage called **"Department Circulars."**

- HOD and Faculty can post urgent notices instantly.
- **Visual Cue:** Notices posted within the last **24 hours** are tagged with a `🆕 New` badge and highlighted in a distinct color.
- Older notices remain visible but without the highlight.

---

## 🛠️ Tech Stack

> *(Update this section based on your actual implementation.)*

| Layer | Technology |
|-------|-----------|
| Frontend | HTML, CSS, JavaScript / React |
| Backend | Node.js / Django / Flask |
| Database | MySQL / PostgreSQL / MongoDB |
| Authentication | JWT / Session-based Auth |
| File Storage | Local / AWS S3 / Firebase Storage |

---

## 🚀 Getting Started

### Prerequisites

- Node.js / Python (depending on backend choice)
- npm / pip
- Database server running locally or remotely

### Installation

```bash
# Clone the repository
git clone https://github.com/your-org/department-portal.git
cd department-portal

# Install dependencies
npm install        # For Node.js backend
# or
pip install -r requirements.txt  # For Python backend

# Configure environment variables
cp .env.example .env
# Fill in DB credentials, JWT secret, storage config, etc.

# Run the development server
npm run dev
# or
python manage.py runserver
```

---

## 📁 Project Structure

```
department-portal/
├── client/                  # Frontend (HTML/CSS/JS or React)
│   ├── pages/
│   │   ├── login.html
│   │   ├── dashboard.html
│   │   ├── repository.html
│   │   └── notice-board.html
│   └── assets/
├── server/                  # Backend API
│   ├── routes/
│   │   ├── auth.js
│   │   ├── upload.js
│   │   ├── approval.js
│   │   ├── search.js
│   │   └── notices.js
│   ├── models/
│   └── middleware/
├── uploads/                 # Uploaded files (local storage)
├── .env.example
├── README.md
└── package.json / requirements.txt
```

---

## 🤝 Contributing

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add: your feature"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request.

Please ensure student-uploaded content follows the approval workflow and file format restrictions before submitting PRs that touch the repository module.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

> Built for the Solve-A-Thon Hackathon 🚀 | Empowering departments with smarter information flow.
