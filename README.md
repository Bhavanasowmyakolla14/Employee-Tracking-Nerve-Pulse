# Employee Tracking & Nerve Pulse HRMS Web Platform

> **Full-Stack Enterprise Workforce Management, Real-Time Attendance Tracking & HRMS Web Platform**

Employee Tracking & Nerve Pulse is a modern, enterprise-grade workforce management platform featuring a **React 19 Web Application**, a high-performance **FastAPI REST Service**, and **Firebase Cloud Functions** with PostgreSQL and Firebase Firestore integration.

---

## 📁 Repository Structure

```text
Employee-Tracking-Nerve-Pulse/
├── frontend/             # React 19 + Vite Web Application (Pure Vanilla CSS, Lucide Icons)
├── backend/              # FastAPI + SQLAlchemy 2.0 + Alembic REST API Service
├── functions/            # Firebase Cloud Functions (v2) for Event Triggers & Alerts
├── docs/                 # System Architecture, Schemas, & Engineering Documentation
├── firebase.json         # Firebase Configuration (Firestore, Storage, Functions, Hosting)
├── firestore.rules       # Cloud Firestore Security Rules
├── firestore.indexes.json# Firestore Composite Indexes
├── storage.rules         # Firebase Cloud Storage Security Rules
├── .firebaserc           # Firebase Project Configuration
├── package.json          # Root Monorepo Scripts
└── README.md             # Project Overview & Setup Guide
```

---

## 🚀 Key Modules & Capabilities

### 💻 Web Application (`frontend/`)
- Built with **React 19**, **Vite 8**, **React Router DOM v7**, and **Lucide React**.
- Modular Vanilla CSS with responsive layouts, glassmorphism aesthetics, and custom design tokens.
- **Admin Portal**:
  - Real-time workforce overview dashboard (Present, Late, WFH, WFO, Leaves).
  - Employee approval workflow for pending registration requests.
  - Leave management with status updates, approvals, and rejections.
  - Attendance management with geofence validation, selfie photos, and CSV report export.
  - Comprehensive HRMS Modules:
    - **Payroll Management**: Monthly payroll batch processing, allowance/deduction breakdowns, and payment execution.
    - **Payslip Generation**: Dynamic PDF payslip rendering and employee distribution.
    - **Salary Structures**: Customizable compensation templates (Basic, HRA, DA, Special Allowance, PF, Professional Tax).
    - **Loans & Salary Advances**: EMI scheduling, approval workflows, and automated payroll deductions.
    - **Performance Management**: KPI goal setting, self-assessments, manager reviews, and appraisal rating cycles.
    - **Separation & Resignation**: Resignation submissions, notice period tracking, asset handovers, and Full & Final (F&F) settlements.
    - **Recruitment**: Job openings, applicant tracking system (ATS), candidate pipelines, and interview scheduling.
    - **Department Management**: Organizational structure, department budgets, and head allocations.
    - **Payment Methods**: Gateway configurations (Razorpay, Stripe) and bulk NEFT/RTGS bank export generation.
    - **Audit Logs**: Immutable activity logging tracking all critical administrative operations.
    - **Settings**: Global company preferences, attendance thresholds, work shifts, and holiday calendars.
  - Work assignments, announcements, meetings, and daily standup reviews.
- **Employee Portal**:
  - Web-based attendance check-in/out with live webcam selfie capture and browser geolocation.
  - Leave application submission and real-time approval status tracking.
  - Self-service payslip viewing and instant PDF download.
  - Loan & salary advance requests with repayment schedules.
  - Performance review self-evaluations and goal tracking.
  - Resignation submission and clearance checklist tracking.
  - Scheduled daily work updates and Jitsi video conference meeting access.

### ⚡ REST API Backend (`backend/`)
- High-performance **FastAPI** service running on **Uvicorn** ASGI.
- **SQLAlchemy 2.0** ORM and **Alembic** schema migrations.
- Dual persistence support: Local PostgreSQL database and Firebase Firestore synchronization.
- Role-based JWT authentication (`pyjwt`, `bcrypt`) and Pydantic v2 data validation schemas.
- ReportLab-powered dynamic PDF generation for corporate payslips.
- Automated payroll computation and F&F settlement calculations.
- Comprehensive test suite covering attendance, leaves, payroll, and API validations.

### 🔔 Cloud Functions (`functions/`)
- Firebase Cloud Functions v2 (Node.js) triggered on Firestore document events.
- Automated email dispatch via **Nodemailer** (SMTP).
- SMS notifications via **Twilio** for registration decisions and workforce alerts.

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 19, Vite 8, React Router v7, Axios, Lucide React, Pure Vanilla CSS |
| **Backend** | Python 3.11+, FastAPI, Uvicorn, SQLAlchemy 2.0, Alembic, Pydantic v2, ReportLab |
| **Database & Cloud** | PostgreSQL / Firebase Firestore, Firebase Cloud Storage |
| **Cloud Functions** | Node.js 20, Firebase Admin SDK, Nodemailer, Twilio |
| **Testing** | Pytest, HTTPX, Vite Vitest / Oxlint |

---

## ⚙️ Quick Start & Setup

### 1. Backend REST API (`backend/`)
```bash
cd backend

# Create and activate virtual environment
python -m venv venv
# On Windows:
.\venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env with your PostgreSQL credentials & JWT secret

# Run database migrations
alembic upgrade head

# Start FastAPI development server
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```
- API Documentation (Swagger UI): `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

### 2. Frontend Web Application (`frontend/`)
```bash
cd frontend

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Set VITE_API_BASE_URL=http://localhost:8000

# Start Vite development server
npm run dev
```
- Frontend Web App: `http://localhost:5173`

### 3. Firebase Cloud Functions (`functions/`)
```bash
cd functions

# Install dependencies
npm install

# Run local emulators
npm run serve

# Deploy to Firebase
firebase deploy --only functions
```

---

## 🧪 Testing

Run backend test suites:
```bash
cd backend
pytest
```

Run frontend production build verification:
```bash
cd frontend
npm run build
```

---

## 🔒 Security & RBAC
- **Authentication**: JWT Bearer token authentication with role-based authorization (`admin` | `employee`).
- **Data Protection**: Sensitive environment variables (`.env`, service account keys) are excluded from version control via `.gitignore`.
- **Firestore & Storage Rules**: Granular Cloud Firestore and Cloud Storage security rules ensuring data segregation.

---

## 📄 License
This project is proprietary and confidential enterprise software.
