# Skipper Limited – Invoice Tracking System

**Corporate Finance Operations | Vendor Invoice & Payment Management**

A centralized web-based application designed to streamline vendor order management, invoice processing, payment tracking, budget allocation, and approval workflows for Skipper Limited's Finance Operations.

---

## 1. Project Overview

The **Invoice Tracking System** is an internal business application developed to improve the management and monitoring of vendor-related financial operations.

The application provides a centralized platform for managing purchase and service orders, vendor invoices, payments, budgets, and approval processes.

It incorporates role-based access, secure authentication, document management, automated email notifications, and approval workflows to improve operational visibility, accountability, and process efficiency.

The system is built using a React and TypeScript frontend, a Python FastAPI backend, and a MySQL relational database.

## 2. Key Objectives

- Centralize vendor invoice and payment management.
- Maintain structured records of purchase and service orders.
- Improve invoice submission, verification, and approval processes.
- Provide visibility into outstanding payments and invoice statuses.
- Manage CAPEX and OPEX budgets through controlled approval workflows.
- Facilitate communication between Finance Operations and IT Head through automated email notifications.
- Maintain supporting financial documents and approval records.
- Improve financial tracking, reporting, and operational transparency.

## 3. Key Features

### 3.1 Dashboard

Provides a centralized overview of financial operations, including:

- Total vendor order amount.
- Outstanding balance and payout information.
- Invoice status summaries.
- Payment and financial activity indicators.

### 3.2 Vendor Management

- Maintain vendor records.
- Store vendor information centrally.
- Associate orders and invoices with vendors.
- Support active and inactive vendor records.

### 3.3 Order Management

- Manage Purchase Orders (PO) and Service Orders (SO).
- Associate orders with vendors and budgets.
- Maintain order amounts and supporting documents.
- Upload and maintain order approval copies.
- View invoices associated with individual orders.

### 3.4 Invoice Management

- Create and manage vendor invoices.
- Associate invoices with their respective orders.
- Support PURCHASE and SERVICE invoice classifications.
- Maintain invoice amounts, dates, and supporting documents.
- Track invoice payment progress.
- Monitor invoice statuses, including:
  - PAID
  - PART_PAID
  - UNPAID
  - OVERDUE
  - ON_HOLD
- Track the date an invoice is sent to Accounts.
- Support invoice Excel bulk-import functionality.

### 3.5 Invoice Approval Workflow

The application includes an email-based invoice approval process.

1. An authorized user submits an invoice for approval.
2. The application creates an approval request.
3. An email notification is sent to the IT Head.
4. The IT Head reviews the request through a secure approval link.
5. The approval link uses a time-limited, one-use token.
6. Once approved, the invoice proceeds through the application's workflow.
7. Accounts receives an automated notification after successful approval.

The workflow also supports bulk invoice approval requests.

### 3.6 Payment Management

- Maintain vendor payment records.
- Associate payments with invoices.
- Track payment amounts and payment dates.
- Support partial and complete payment tracking.
- Monitor outstanding invoice balances.

### 3.7 Budget Management

The application supports two primary budget classifications:

**OPEX – Operational Expenditure**

- Manage OPEX budget categories.
- Maintain hierarchical subcategory allocations.
- Support manually entered subcategories.
- Track planned and approved allocations.
- View detailed subcategory information.

**CAPEX – Capital Expenditure**

- Manage CAPEX budget records.
- Track planned and approved budget amounts.
- Maintain supporting approval documentation.

### 3.8 Budget Approval Workflow

Budget creation, updates, and allocation requests are managed through an IT Head approval workflow.

- Submit budget requests for approval.
- Support budget creation and update requests.
- Allow the IT Head to determine the approved amount within the permitted limit.
- Manage OPEX subcategory allocation requests.
- Maintain pending, approved, and rejected request statuses.
- Attach supporting approval documents.
- Send email notifications to Accounts after successful approval.

### 3.9 Document Management

The application supports document uploads associated with financial operations, including:

- Invoice copies.
- Order approval copies.
- Budget approval documents.
- OPEX subcategory approval documents.
- Supporting Excel files for bulk invoice imports.

Uploaded documents are maintained by the backend and associated with their respective business records.

## 4. Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React |
| Programming Language | TypeScript |
| Frontend Build Tool | Vite |
| Backend | Python |
| Backend Framework | FastAPI |
| ORM | SQLAlchemy |
| Database | MySQL |
| Database Migrations | Alembic |
| Authentication | JWT |
| Password Security | Argon2 |
| Email Notifications | SMTP |
| API Documentation | Swagger UI |

### Development Environment

| Component | Development Version |
|---|---|
| Python | 3.12.10 |
| Node.js | 24.21.0 |
| npm | 11.19.0 |
| FastAPI | 0.143.0 |
| SQLAlchemy | 2.1.4 |
| Alembic | 1.20.0 |
| MySQL | MySQL Server |

## 5. System Architecture

The application follows a frontend-backend-database architecture.

```text
                USERS
                  |
                  |
          React + TypeScript
             Frontend
                  |
             HTTP / REST
                  |
                  |
          FastAPI Backend
                  |
       -----------------------
       |          |          |
    API Routes  Services   Security
       |          |          |
       |      Email Service  JWT
       |
    SQLAlchemy ORM
       |
       |
    MySQL Database
       |
       |
    Financial Records
```

### Architecture Components

**Frontend**

Responsible for the user interface, navigation, data presentation, form submissions, and interaction with backend APIs.

**Backend**

Responsible for business logic, validation, authentication, approval workflows, email notifications, document handling, and database operations.

**Database**

Stores vendor, order, invoice, payment, budget, user, and approval-related records.

**Email Service**

Handles automated email notifications for approval workflows and communication with the relevant departments.

## 6. Project Directory Structure

The repository is organized into separate frontend and backend applications.

```text
Invoice_traking-/
│
├── backend/
│   │
│   ├── alembic/
│   │   └── versions/
│   │
│   ├── app/
│   │   ├── api/
│   │   │   └── routes/
│   │   │
│   │   ├── core/
│   │   │
│   │   ├── models/
│   │   │
│   │   ├── schemas/
│   │   │
│   │   ├── services/
│   │   │
│   │   ├── uploads/
│   │   │
│   │   └── main.py
│   │
│   ├── create_it_head.py
│   ├── requirements.txt
│   └── .env.example
│
├── frontend/
│   │
│   ├── public/
│   │
│   ├── src/
│   │   ├── pages/
│   │   ├── styles/
│   │   ├── components/
│   │   └── App.tsx
│   │
│   ├── package.json
│   └── vite.config.ts
│
├── .gitignore
└── README.md
```

*Note: The structure above illustrates the main application components. Some directories and files may vary as the project evolves.*

## 7. Installation and Setup

### Prerequisites

Install the following software before running the application:

- Python 3.12 or compatible version.
- Node.js and npm.
- MySQL Server.
- Git.
- Visual Studio Code (recommended).

### 7.1 Clone the Repository

```bash
git clone https://github.com/SKAIcell/Invoice_traking-.git
```

Navigate into the project directory:

```bash
cd Invoice_traking-
```

### 7.2 Backend Setup

Open a terminal and navigate to the backend directory:

```bash
cd backend
```

Create a Python virtual environment:

```bash
python -m venv .venv
```

Activate the virtual environment on Windows:

```cmd
.venv\Scripts\activate
```

Install backend dependencies:

```bash
pip install -r requirements.txt
```

### 7.3 Database Configuration

Create the MySQL database:

```sql
CREATE DATABASE invoice_tracker;
```

Configure the database connection using the environment variables expected by the backend configuration.

### 7.4 Environment Configuration

Create a local `.env` file in the backend directory.

Configure the required settings according to `backend/app/core/config.py`.

These include:

- Database connection details.
- JWT authentication configuration.
- SMTP host and port.
- SMTP username and password.
- Email sender configuration.
- IT Head email address.
- Accounts email address.
- Public backend URL used for approval links.

**Important:** Never commit real credentials, passwords, JWT secrets, or production environment files to Git.

### 7.5 Database Migrations

Run the database migrations:

```bash
alembic upgrade head
```

To verify the current migration:

```bash
alembic current
```

To view migration history:

```bash
alembic history
```

### 7.6 Start the Backend

From the backend directory:

```bash
python -m uvicorn app.main:app --reload
```

Backend development server:

```text
http://127.0.0.1:8000
```

Swagger API documentation:

```text
http://127.0.0.1:8000/docs
```

### 7.7 Frontend Setup

Open another terminal and navigate to the frontend directory:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Frontend development server:

```text
http://localhost:5173
```

## 8. Database Management

The application uses MySQL for persistent data storage.

SQLAlchemy manages database interactions, while Alembic manages schema changes through version-controlled migrations.

Database entities include:

- Users
- Vendors
- Budgets
- Budget approval requests
- Budget subcategories
- Subcategory approval requests
- Orders
- Invoices
- Invoice approval requests
- Payments

Database changes should be managed through Alembic migrations rather than manually modifying the production database schema.

## 9. Authentication and Security

The application incorporates security measures to protect internal financial information.

Key security features include:

- JWT-based authentication.
- Password hashing using Argon2.
- Role-based authorization.
- Backend-side request validation.
- Secure approval tokens.
- Time-limited approval links.
- One-use approval tokens.
- Environment-based configuration.
- Controlled document upload handling.
- Configured Cross-Origin Resource Sharing (CORS).

Production deployment should use HTTPS, restricted network access, secure secret management, and appropriate database permissions.

## 10. Email Notification System

The application uses an SMTP-based email service for automated notifications.

Email functionality supports:

- IT Head approval requests.
- Invoice approval notifications.
- Budget approval notifications.
- Accounts notifications after successful approval.

Email configuration is maintained through environment variables.

Notification failures should be logged and handled without unintentionally reversing an approval that has already been committed to the database.

## 11. Deployment Considerations

The application is designed with a separate frontend and backend, making it suitable for deployment in a Linux-based server environment.

A production deployment should include:

1. Linux Ubuntu server environment.
2. Containerized frontend and backend services where appropriate.
3. MySQL database configuration.
4. Production environment variables and secret management.
5. Persistent storage for uploaded documents.
6. Reverse proxy configuration.
7. HTTPS and SSL certificate configuration.
8. Firewall and network access restrictions.
9. Database backup and recovery procedures.
10. Application logging and monitoring.

Docker can be used to package the application components and provide a consistent deployment environment.

**Production deployment configuration must be prepared and reviewed according to the company's IT Infrastructure and IT Security requirements.**

## 12. Version Control

The project is maintained using Git and GitHub.

Repository:

https://github.com/SKAIcell/Invoice_traking-

Main development branch:

```text
main
```

Example Git commands:

```bash
git status
git add -A
git commit -m "Describe your changes"
git push origin main
```

Sensitive configuration files, local database dumps, uploaded financial documents, and generated temporary files are excluded through `.gitignore`.

## 13. Future Enhancements

Potential future improvements include:

- Advanced financial reporting and analytics.
- Enhanced dashboard visualizations.
- Additional audit and activity tracking.
- Expanded notification and monitoring capabilities.
- Production deployment monitoring.
- Automated backup and recovery enhancements.
- Further workflow automation.

## 14. Conclusion

The Skipper Limited Invoice Tracking System provides a centralized platform for managing vendor-related financial operations.

By integrating order management, invoice processing, payment tracking, budget management, document handling, and approval workflows, the application aims to improve operational efficiency, financial visibility, and accountability across Finance Operations.

The modular architecture and use of established development technologies provide a foundation for future enhancements and deployment within the company's IT infrastructure.

---

**Project:** Invoice Tracking System  
**Organization:** Skipper Limited  
**Department:** Finance Operations  
**Application Type:** Internal Business Web Application  
**Repository:** https://github.com/SKAIcell/Invoice_traking-  
**Technology:** React · TypeScript · FastAPI · SQLAlchemy · MySQL
