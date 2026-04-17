#Feature Flag System (Multi-Tenant SaaS)

A full-stack multi-tenant feature flag management system built using the MERN stack.
This application allows organizations to control feature rollouts dynamically without deploying new code.

---

##What Problem This Solves

In real-world products, not every feature should be available to all users at once.

This system allows:
- Enabling/disabling features per organization
- Safe feature rollout
- Testing features for specific clients
- Avoiding redeployment for small changes

---

##Architecture Overview

feature-flag-system/
├── backend/                  → Node.js + Express + MongoDB Atlas
├── frontend-superadmin/      → Super Admin Dashboard
├── frontend-admin/           → Organization Admin Panel
└── frontend-user/            → Feature Checker UI

---

##User Roles

###Super Admin
- Creates organizations
- Manages global system

###Organization Admin
- Registers using organization ID
- Creates & manages feature flags

###End User
- Checks whether a feature is enabled

---

##Tech Stack

- Frontend: React 18, Vite, React Router
- Backend: Node.js, Express
- Database: MongoDB Atlas
- Auth: JWT + bcrypt
- HTTP: Axios

---

##MongoDB Setup (Atlas)

1. Create a free cluster in MongoDB Atlas
2. Create a database user
3. Whitelist IP (0.0.0.0/0 for development)
4. Use connection string:

mongodb+srv://<username>:<password>@cluster.mongodb.net/featureflagdb

---

##Backend Setup

cd backend
npm install

Create .env file:

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
SUPER_ADMIN_EMAIL=superadmin@system.com
SUPER_ADMIN_PASSWORD=admin123

Seed initial data:

npm run seed

Run server:

npm run dev

---

##Frontend Setup

Run each frontend in separate terminals:

Super Admin:
cd frontend-superadmin
npm install
npm run dev

Org Admin:
cd frontend-admin
npm install
npm run dev

End User:
cd frontend-user
npm install
npm run dev

---

##Default Login Credentials

Super Admin: superadmin@system.com / admin123
Org Admin: nk@gmail.com / nk123
Org Admin: user@byepo.com / user123

---

##Application Flow

1. Super Admin creates organization and shares org ID
2. Org Admin registers using org ID and manages feature flags
3. End User checks feature status using org ID + feature key

---

##API Overview

Auth:
POST /api/auth/login
POST /api/auth/signup

Organizations:
GET /api/orgs
POST /api/orgs

Feature Flags:
GET /api/flags
POST /api/flags
PUT /api/flags/:id
DELETE /api/flags/:id
GET /api/flags/check?feature_key=xxx&org_id=yyy

---

##Key Concepts

- Multi-tenant architecture
- Role-based access control
- JWT authentication
- REST APIs
- Feature toggling

---
