<p align="center">
  <h1 align="center">🏗️ Cliberduche Corporation — Company Portal</h1>
  <p align="center">
    A full-stack web platform for a construction company, featuring a public-facing website with CMS and an internal operations management system.
  </p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18.3-61DAFB?style=flat-square&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/Laravel-12-FF2D20?style=flat-square&logo=laravel&logoColor=white" />
  <img src="https://img.shields.io/badge/Vite-5-646CFF?style=flat-square&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/TailwindCSS-3.4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/Sanctum-4-FF2D20?style=flat-square&logo=laravel&logoColor=white" />
  <img src="https://img.shields.io/badge/PHPUnit-11-3C9CD7?style=flat-square&logo=php&logoColor=white" />
</p>

---

## 📌 Overview

**Cliberduche Corporation Portal** is a full-stack web application built for a construction company. It serves two audiences:

1. **Public Website** — A dynamic, CMS-driven site showcasing the company's services, projects, team, and contact information.
2. **Internal System Portal** — A role-based admin panel for managing content, procurement, inventory, users, and system operations.

The entire application is built with a **React** SPA frontend consuming a **Laravel 12** REST API backend, following modern full-stack development practices.

---

## ✨ Key Features

### 🌐 Public Website
- **Home** — Hero carousel with animated sections
- **About Us** — Company profile, mission/vision, organizational chart
- **Services** — Dynamic listing of construction services
- **Projects** — Portfolio with gallery, before/after images, and public/private visibility
- **Resources** — Machinery fleet and development sites showcase
- **Contact** — Inquiry form with rate-limiting protection
- **FAQ** — Frequently asked questions managed via CMS
- **Interactive FAQ Widget** — Searchable FAQ panel with dark/light theme support; unmatched queries route to the Contact page as pre-filled inquiries
- **Company Profile Download** — Secure, tokenized PDF download links

### 🔒 System Portal (Admin Panel)
- **Dashboard** — Statistics overview with Recharts data visualization and real-time system alerts
- **CMS Modules** — Full CRUD management for About, Services, Projects, FAQs, Contact, and Company Profile
- **Inquiry Management** — View, archive, and manage client inquiries
- **Procurement Workflow** — Request creation → status tracking → PDF report generation (via DomPDF)
- **Inventory Management** — Categories, items, stock in/out tracking
- **Organization Manager** — Hierarchical team structure with drag-and-drop reordering
- **User & Role Management** — Spatie Permission-based RBAC with granular permissions
- **Backup Management** — System backup creation, download, and deletion (permission-gated)
- **Account Settings** — Password management and profile configuration
- **Real-time Notifications** — Laravel-powered notification system

---

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 18, React Router 6, Vite 5, TailwindCSS 3, Bootstrap 5, Framer Motion |
| **Backend** | Laravel 12, PHP 8.2+, Laravel Sanctum (token auth), Spatie Permission (RBAC) |
| **Database** | SQLite (dev) / MySQL (prod), 25+ migrations, Eloquent ORM |
| **Testing** | PHPUnit 11, 19+ feature test suites |
| **PDF Generation** | DomPDF (procurement reports, company profiles) |
| **Data Viz** | Recharts (dashboard analytics) |
| **Real-time** | Laravel Reverb, Pusher, Laravel Echo |
| **Dev Tools** | ESLint, Laravel Pint, Faker (seeders/factories) |

---

## 🏗️ Architecture

```
CB-website/
├── frontend/                    # React SPA
│   └── src/
│       ├── api/                 # Axios API service layer
│       ├── components/          # 24 reusable components
│       ├── context/             # Auth, Loading, Settings providers
│       ├── layouts/             # Public Layout + System Layout
│       ├── lib/                 # Axios instance & cache management
│       ├── pages/               # 10 public pages + 14 system pages
│       └── utils/               # Helper utilities
│
├── backend/                     # Laravel 12 API
│   ├── app/
│   │   ├── Http/Controllers/    # 28 API controllers
│   │   ├── Models/              # Eloquent models
│   │   ├── Notifications/       # Event-driven notifications
│   │   └── Http/Resources/      # API resource transformers
│   ├── database/
│   │   ├── migrations/          # 25+ schema migrations
│   │   ├── seeders/             # 8 data seeders
│   │   └── factories/           # 5 model factories
│   ├── routes/api.php           # 100+ RESTful API endpoints
│   └── tests/Feature/           # 19 feature test suites
```

---

## 🔐 Security & Access Control

- **Authentication**: Laravel Sanctum token-based authentication
- **Authorization**: Spatie Permission RBAC with 4 roles (Admin, Project Manager, Site Engineer, Staff)
- **Route Protection**: Middleware-based role and permission guards on both frontend and backend
- **Rate Limiting**: Throttle middleware on public endpoints (e.g., contact form: 5 requests/min)
- **API Security**: CORS configuration, CSRF protection, input validation on all endpoints

---

## 🧪 Testing

The backend includes **19+ automated feature tests** covering:

| Test Suite | Coverage |
|-----------|----------|
| `AuthenticationTest` | Login, registration, session management |
| `RbacTest` | Role-based access control enforcement |
| `ProcurementWorkflowTest` | Full procurement lifecycle |
| `ProcurementReportTest` | PDF report generation |
| `SecurityDemoTest` | Security vulnerability protection |
| `DatabaseConsistencyTest` | Data integrity validation |
| `InventoryTest` | Stock management operations |
| `SystemAlertsTest` | Alert creation and resolution |
| `BackupRbacTest` | Permission-gated backup operations |
| `FaqEndpointTest` | FAQ CRUD operations |
| `CompanyProfileTest` | Company profile management |
| `OrganizationMemberTest` | Team structure management |
| `RoleManagementTest` | Role CRUD and permission assignment |
| `DashboardTest` | Dashboard statistics API |
| `SystemCapabilitiesTest` | End-to-end system validation |

```bash
# Run all tests
cd backend
php artisan test
```

---

## 🚀 Getting Started

### Prerequisites
- PHP 8.2+
- Composer
- Node.js 18+
- npm

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/CB-website.git
cd CB-website

# Backend setup
cd backend
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed

# Frontend setup
cd ../frontend
npm install

# Run the application
# Terminal 1 — Backend
cd backend
php artisan serve

# Terminal 2 — Frontend
cd frontend
npm run dev
```

The frontend runs on `http://localhost:5173` and the API on `http://localhost:8000`.

---

## 📊 API Overview

The backend exposes **100+ RESTful endpoints** organized into:

| Module | Endpoints | Description |
|--------|-----------|-------------|
| **Auth** | `POST /login`, `POST /register`, `POST /logout` | Sanctum token authentication |
| **CMS** | `/services`, `/projects`, `/faqs`, `/inquiries`, `/page-contents` | Public content management |
| **System** | `/system/dashboard-stats`, `/system/users`, `/system/roles` | Internal administration |
| **Procurement** | `/procurement`, `/procurement/{id}/status`, `/procurement/report` | Procurement workflow + PDF |
| **Inventory** | `/inventory-categories`, `/inventory-items`, `add-stock`, `remove-stock` | Stock management |
| **Company Profile** | `/company-profile`, `/company-profile/generate-link` | Profile management + secure downloads |
| **Notifications** | `/notifications`, `/notifications/{id}/read` | Real-time notification system |
| **Backups** | `/system/backups` | Database backup management |

All protected endpoints require `Authorization: Bearer <token>` header.

---

## 👤 Default Accounts (Seeded)

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@gmail.com | password |
| Project Manager | pm@gmail.com | password |
| Site Engineer | engineer@gmail.com | password |
| Staff | staff@gmail.com | password |

> Run `php artisan migrate --seed` to populate default data.

---

## 📸 System Showcase

Screenshots of the internal management system built during OJT, demonstrating the key operational modules and role-based access control.

### 👤 User Management
> Manage system users with role assignments. Admins can add, edit, and assign roles (Admin, Project Manager, Site Engineer, Staff) to control access across the platform.

<p align="center">
  <img src="ojt/User-Management.png" alt="User Management Panel" width="800" />
</p>

### 🔐 Role & Permission Manager
> A granular RBAC system powered by Spatie Permissions. Each role card displays its permission count and access highlights — making it easy to audit and manage what each role can do across 25+ system permissions.

<p align="center">
  <img src="ojt/Role-and-Permission_Manager.png" alt="Role and Permission Manager" width="800" />
</p>

### 📋 Procurement — Admin View
> The Admin procurement dashboard with full visibility: active/completed request tabs, search functionality, status tracking (Submitted, Processing), and access to **Generate Report** for PDF export via DomPDF.

<p align="center">
  <img src="ojt/Procurement(admin).png" alt="Procurement - Admin View" width="800" />
</p>

### 📋 Procurement — Project Manager View
> The same Procurement module viewed as a Project Manager role — demonstrating the RBAC in action. The sidebar adapts to show only the modules the PM role has access to, and the report generation tab is hidden based on permissions.

<p align="center">
  <img src="ojt/Procurement(ProjectManager).png" alt="Procurement - Project Manager View" width="800" />
</p>

### 🧪 Automated Backend Testing
> A comprehensive suite of 19+ automated feature test suites built with PHPUnit. These tests rigorously validate core functionalities such as Role-Based Access Control (RBAC), end-to-end procurement workflows, secure API authentication, database consistency, and system vulnerability protection—ensuring the system remains highly reliable.

<p align="center">
  <img src="ojt/BackendTestResult.png" alt="Backend Test Results" width="800" />
</p>

---

## 👥 Team

This project was developed as a team deliverable during our OJT (On-the-Job Training) internship. While this was a group effort, I served as the primary developer — responsible for the full-stack architecture, backend API, authentication, RBAC, testing, and the majority of frontend system modules. Contributions from team members are reflected in the git history.

---

## 📄 License

This project was developed during an OJT internship for Cliberduche Corporation.

---

<p align="center">
  Built with ❤️ using React + Laravel
</p>
