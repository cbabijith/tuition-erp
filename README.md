# ERPNext Based Institute Management System

ERPNext will be used as the administrative and operational management system for the institute. While Moodle manages learning activities, course materials, assignments, and exams, ERPNext will manage the administrative operations.

This combination creates a complete digital management system for the tuition center.

---

## Modules Required for Tuition Center

The following **8 modules** cover 100% of the tuition center requirements:

| # | Module | Purpose |
|---|---|---|
| 1 | **Education** | Student records, courses, subjects, enrollment, fee structure, fee generation |
| 2 | **CRM** | Lead management, enquiries, admission pipeline, follow-ups |
| 3 | **Accounting** | Fee collection, payments, invoices, P&L, balance sheet, branch-wise financials |
| 4 | **HR & Payroll** | Employee database, salary structures, payroll processing, salary slips |
| 5 | **Attendance & Leave** | Staff/teacher attendance, leave requests/approvals, leave balance tracking |
| 6 | **Assets** | Institute asset tracking across branches, allocation, maintenance history |
| 7 | **Document Management** | Student/employee document storage linked to records |
| 8 | **Reports & Dashboards** | Fee collection, pending fees, defaulter tracking, management KPIs |

All 8 modules come pre-installed with ERPNext v15. No additional module installation needed.

---

## Implementation Phases

### Phase 1: System Setup & Configuration

**5 Core Items:**
1. **Company, currency, fiscal year** - Set up company (REG Learning Center), currency (KWD), fiscal year ✅ DONE
2. **Branches** - Configure branch locations (Head Office + additional branches) ✅ DONE (Jaleeb, Mangaf)
3. **Roles & permissions** - Super Admin, Branch Admin, Staff roles ✅ DONE
4. **Email (SMTP)** - Configure outgoing email server ⬜ PENDING
5. **Arabic language** - Enable Arabic translation + RTL layout ⬜ PENDING

**5 Additional Items:**
6. **System settings** - Timezone (Asia/Kuwait), date format, number format ⬜ PENDING
7. **Fiscal year** - Create fiscal year for the institute ✅ DONE (2025-2026)
8. **Cost centers** - Set up branch-wise cost centers for accounting ⬜ PENDING
9. **Print formats / Letterhead** - Institute logo, header for fee receipts & documents ⬜ PENDING
10. **Number series** - Configure invoice numbers, student IDs, etc. ⬜ PENDING

**Total: 10 items (5 core + 5 additional)**
**Completed: 4/10 | Pending: 6/10**

**Additional work completed:**
- ✅ Company: REG Learning Center created (Abbr: REG, Country: Kuwait, Currency: KWD, Domain: Education)
- ✅ Address: Head Office - Floor No. 1, Building No. 172, Street 25, Block 4, Jaleeb Al Shuyoukh, Kuwait
- ✅ Fiscal Year: 2025-2026 (Jul 1, 2025 → Jun 30, 2026)
- ✅ Branches: Jaleeb, Mangaf created
- ✅ Roles: Super Admin (full access), Branch Admin (student/fee/CRM/HR management), Staff (limited read/write access)
- ✅ Permissions: Branch Admin gets 15 doctype permissions, Staff gets 5 doctype permissions
- ✅ Default company & currency set in Global Defaults
- ✅ Default "ABC" company deleted
- ✅ 11 unwanted workspaces hidden (Manufacturing, Quality, Buying, Stock, Projects, Support, Website, Tools, ERPNext Integrations, Build, Welcome Workspace)
- ✅ 11 visible workspaces retained (Home, Accounting, Financial Reports, Receivables, Payables, CRM, Assets, Selling, Integrations, ERPNext Settings, Users)

### Phase 2: Education Module (First functional module)
- Academic year & term setup
- Create programs/courses (Physics, Chemistry, Maths, combos)
- Configure fee structures (subject-wise, combo packages)
- Set up fee schedules (monthly billing)
- Student enrollment workflow

### Phase 3: CRM Module
- Lead capture (enquiries from parents/students)
- Follow-up activities and reminders
- Lead → Opportunity → Student Admission conversion
- Admission pipeline tracking

### Phase 4: Accounting Module
- Chart of accounts setup
- Fee invoicing workflow (linked to Education module)
- Payment entry recording (cash, bank, digital)
- Outstanding balance tracking
- Branch-wise financial reports

### Phase 5: HR & Payroll Module
- Employee master (teachers, admin staff)
- Salary structures (Kuwait-specific components)
- Monthly payroll processing
- Salary slip generation

### Phase 6: Attendance & Leave Module
- Employee attendance tracking
- Leave policy configuration
- Leave application and approval workflow
- Attendance reports by branch

### Phase 7: Asset Management Module
- Asset registration (computers, projectors, furniture)
- Asset allocation to branches
- Maintenance scheduling
- Depreciation tracking

### Phase 8: Document Management & Reports
- Document templates (fee receipts, salary slips, admission letters)
- Custom dashboards (fee collection, defaulters, attendance)
- Email notification templates (payment confirmation, fee due reminders)
- Management reports

### Phase 9: Moodle Integration (Custom Development)
- Student sync from ERPNext → Moodle
- API integration setup
- Testing and deployment

---

## Table of Contents

- [Overview](#overview)
- [Modules Required for Tuition Center](#modules-required-for-tuition-center)
- [Implementation Phases](#implementation-phases)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Deployment on a New Server](#deployment-on-a-new-server)
- [ERPNext Features for Institute Management](#erpnext-features-for-institute-management)
  - [1.1 Student Management](#11-student-management)
  - [1.2 Course & Subject Enrollment](#12-course--subject-enrollment)
  - [1.3 Fee Structure Management](#13-fee-structure-management)
  - [1.4 Monthly Fee Generation](#14-monthly-fee-generation)
  - [1.5 Fee Collection & Payment Tracking](#15-fee-collection--payment-tracking)
  - [1.6 Fee Pending & Defaulter Tracking](#16-fee-pending--defaulter-tracking)
  - [1.7 Multi-Branch Management](#17-multi-branch-management)
  - [1.8 Staff & HR Management](#18-staff--hr-management)
  - [1.9 CRM (Lead & Admission Management)](#19-crm-lead--admission-management)
  - [1.10 Document Management](#110-document-management)
  - [1.11 Asset Management](#111-asset-management)
  - [1.12 Finance & Accounting](#112-finance--accounting)
  - [1.13 Payroll Management](#113-payroll-management)
  - [1.14 Dashboards & Reports](#114-dashboards--reports)
  - [1.15 Payment Email Notifications](#115-payment-email-notifications)
- [Moodle and ERPNext Integration](#moodle-and-erpnext-integration)
- [Server Setup & Configuration](#server-setup--configuration)
- [Feature Feasibility Analysis](#feature-feasibility-analysis)

---

## Overview

| System | Function |
|---|---|
| **Moodle** | Learning Management System (course materials, assignments, exams, attendance, live classes) |
| **ERPNext** | Administration and Institute Management (students, fees, HR, payroll, accounting, CRM, assets) |

ERPNext manages:
- Student records
- Lead and admission management (CRM)
- Fee management
- Payments and accounting
- Staff, HR and payroll management
- Attendance and leave
- Document management
- Asset management
- Multi-branch operations
- Reports and dashboards

---

## Tech Stack

| Component | Technology |
|---|---|
| ERP System | ERPNext v15 (Frappe Framework) |
| Database | MariaDB 10.6 |
| Cache / Queue | Redis 6.2 |
| Containerization | Docker + Docker Compose |
| OS | Ubuntu (WSL2 / Dedicated Server) |
| LMS (Separate) | Moodle |
| Currency | KWD (Kuwaiti Dinar) |
| Language Support | English + Arabic (RTL) |

---

## Quick Start

### Prerequisites

- Docker
- Docker Compose
- Git

### Steps

```bash
# 1. Clone the repository
git clone git@github.com:cbabijith/tuition-erp.git
cd tuition-erp

# 2. Start all services
docker compose up -d

# 3. Wait ~30 seconds for MariaDB to initialize, then create the site
docker compose exec backend bench new-site erpnext.localhost \
  --mariadb-root-password admin \
  --admin-password admin \
  --db-host db

# 4. Fix Redis configuration
docker compose exec backend python3 -c "
import json
for f in ['sites/erpnext.localhost/site_config.json', 'sites/common_site_config.json']:
    d = json.load(open(f))
    d['redis_cache'] = 'redis://redis:6379/0'
    d['redis_queue'] = 'redis://redis:6379/1'
    d['redis_socketio'] = 'redis://redis:6379/2'
    json.dump(d, open(f, 'w'), indent=1)
    print(f'Updated {f}')
"

# 5. Install ERPNext app
docker compose exec backend bench --site erpnext.localhost install-app erpnext

# 6. Restart all services to apply Redis config
docker compose restart

# 7. Verify
curl -sI http://localhost:8080 | head -5
```

### Access

- **URL**: `http://localhost:8080`
- **Username**: `Administrator`
- **Password**: `admin`

> **Note**: Change the default password immediately after first login for production use.

---

## Deployment on a New Server

```bash
# 1. SSH into your server
ssh user@your-server-ip

# 2. Install Docker + Docker Compose
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
# Log out and back in for docker group to take effect

# 3. Clone the repository
git clone git@github.com:cbabijith/tuition-erp.git
cd tuition-erp

# 4. Start all services
docker compose up -d

# 5. Wait ~30 seconds, then create the site
docker compose exec backend bench new-site erpnext.localhost \
  --mariadb-root-password admin \
  --admin-password admin \
  --db-host db

# 6. Fix Redis configuration
docker compose exec backend python3 -c "
import json
for f in ['sites/erpnext.localhost/site_config.json', 'sites/common_site_config.json']:
    d = json.load(open(f))
    d['redis_cache'] = 'redis://redis:6379/0'
    d['redis_queue'] = 'redis://redis:6379/1'
    d['redis_socketio'] = 'redis://redis:6379/2'
    json.dump(d, open(f, 'w'), indent=1)
    print(f'Updated {f}')
"

# 7. Install ERPNext app
docker compose exec backend bench --site erpnext.localhost install-app erpnext

# 8. Restart all services
docker compose restart

# 9. Verify
curl -sI http://localhost:8080 | head -5
```

Access at `http://your-server-ip:8080`

### Production Considerations

- Use a real domain name instead of `erpnext.localhost`
- Set strong passwords (not `admin`)
- Add SSL/HTTPS (Let's Encrypt + reverse proxy or Caddy)
- Change `restart_policy` from `on-failure` to `unless-stopped`
- Set up automated database backups
- Configure SMTP for email notifications

---

## ERPNext Features for Institute Management

### 1.1 Student Management

ERPNext will maintain a centralized student database. ERPNext acts as the master student database for the institute.

**Student profiles will include:**
- Personal details
- Parent contact information
- Admission details
- Previous academic information
- Enrolled subjects
- Branch location
- Payment history

Students can enroll in multiple subjects such as Physics, Chemistry, Mathematics etc, and combinations of subjects.

---

### 1.2 Course & Subject Enrollment

Students can join courses subject-wise.

**Example:**

| Student | Course | Monthly Fee |
|---|---|---|
| Student A | Physics | KWD 20 |
| Student A | Chemistry | KWD 25 |

ERPNext can maintain subject and package enrollment records for students based on configured academic and fee structures.

---

### 1.3 Fee Structure Management

ERPNext will manage the complete fee structure.

**Example configuration:**

| Course | Fee |
|---|---|
| Physics | KWD 20 |
| Chemistry | KWD 25 |
| Combo 1 | KWD 40 |

> **Note**: Combination packages must be configured as separate courses (Example: Physics + Chemistry package: KWD 40).

**The system supports:**
- Subject-wise fees
- Combination discounts
- Monthly billing cycles
- Custom fee structures

---

### 1.4 Monthly Fee Generation

Periodic fee invoicing can be configured within ERPNext based on the institute's billing requirements.

**Example:**

| Field | Value |
|---|---|
| Student | Rahul |
| Physics | KWD 20 |
| Chemistry | KWD 25 |
| Discount | KWD 5 |
| **Total Fee** | **KWD 40** |

Invoices can be generated periodically through ERPNext billing workflows.

---

### 1.5 Fee Collection & Payment Tracking

ERPNext will record payments received from students.

**Supported payment methods:**
- Cash
- Bank transfer
- Digital payments

> Digital payment gateway integration is subject to the availability and compatibility of local payment provider APIs.

**ERPNext automatically tracks:**
- Total fee
- Amount paid
- Outstanding balance

---

### 1.6 Fee Pending & Defaulter Tracking

ERPNext will generate reports showing:

| Student | Total Fee | Paid | Due |
|---|---|---|---|
| Rahul | 40 | 20 | 20 |

**Reports available:**
- Monthly fee collection
- Pending fees
- Defaulters list
- Student payment history

---

### 1.7 Multi-Branch Management

ERPNext supports management of multiple branches.

**Example:**

| Branch | Students |
|---|---|
| Branch A | 120 |
| Branch B | 80 |

**Features include:**
- Branch-wise student management
- Branch-wise fee reports
- Branch-wise financial and collection reports
- Central management dashboard

---

### 1.8 Staff & HR Management

ERPNext can manage institute staff similar to the previously proposed HR system.

#### Employee Database
- Teacher profiles
- Administrative staff profiles
- Employment details
- Document storage

#### Attendance Management
- Staff & HR Attendance
- Teacher Attendance
- Attendance reports
- Attendance tracking by branch
  > Biometric integration is subject to the hardware API only

#### Leave Management
- Leave requests
- Leave approvals
- Leave balance tracking

#### Payroll Management
- Salary structure management
- Monthly payroll processing
- Salary slips and payroll reports

#### Role-Based Access
- Super Admin
- Branch Admin
- Staff login

Permissions are controlled based on roles.

---

### 1.9 CRM (Lead & Admission Management)

ERPNext includes a built-in CRM module that helps manage student and parent enquiries before admission.

**Features include:**
- Lead management for prospective students
- Parent enquiry tracking
- Follow-up reminders and activities
- Admission pipeline monitoring
- Conversion tracking from enquiry to admission

This helps administrative staff organize admissions and follow-up activities efficiently.

---

### 1.10 Document Management

ERPNext provides centralized document storage linked to student and employee records.

**Documents that can be stored include:**
- Student identification documents
- Academic records and certificates
- Employee documents
- Other administrative records

Documents are securely stored and accessible based on user permissions.

---

### 1.11 Asset Management

ERPNext can track institute assets across multiple branches.

**Examples include:**
- Computers and laptops
- Projectors and smart boards
- Printers and networking equipment
- Furniture and office equipment

**Features include:**
- Asset registration
- Asset allocation tracking
- Branch-wise asset records
- Asset maintenance history

---

### 1.12 Finance & Accounting

ERPNext includes a complete accounting system integrated with student fee management.

**Features include:**
- Accounts Receivable (Student Fees)
- Accounts Payable (Vendor Payments)
- General Ledger
- Payment Entry Management
- Income & Expense Tracking
- Profit & Loss Reports
- Balance Sheet Reports
- Branch-wise Financial Reporting

This allows management to maintain financial records within the same system.

---

### 1.13 Payroll Management

ERPNext can manage employee payroll and salary processing.

**Features include:**
- Employee salary structures
- Monthly payroll processing
- Salary slips
- Payroll reports
- Leave integration with payroll
- Employee attendance integration

Payroll calculations can be configured according to the institute's salary policies.

---

### 1.14 Dashboards & Reports

ERPNext provides powerful management dashboards including:
- Total students
- Monthly fee collection
- Pending fees
- Staff/Teacher attendance reports
- Admission and CRM reports
- Financial reports
- Payroll reports
- Asset reports

These dashboards help management monitor the institute efficiently.

---

### 1.15 Payment Email Notifications

- Payment Email Notifications to students
- Fee Due Reminder Emails to students
  > Subject to SMTP email service availability and configuration.

---

## Moodle and ERPNext Integration

The system will integrate Moodle (Learning Management System) with ERPNext (Institute Management System). Each system will perform the functions it is designed for, ensuring system stability, maintainability, and scalability.

| System | Function |
|---|---|
| Moodle | Learning Management System |
| ERPNext | Administration and Institute management |

### Integration Workflow

Student admission and administrative processes will be managed through ERPNext.

**After admission:**

1. A student record will be created in ERPNext.
2. Basic student information (name, email address, and username) can be synchronized to Moodle through the configured ERPNext–Moodle integration.
3. Student enrollment into Moodle subjects/courses will be performed by authorized administrators manually.
4. Students will receive login credentials for the Moodle learning platform.
5. ERPNext access will be restricted to authorized institute administrators and staff.

### Learning Activities

Students will access the following through Moodle:
- Study materials
- Assignments
- Online examinations
- Attendance tracking
- Learning progress tracking
- Live classes

### Scope of Integration

The integration scope includes synchronization of basic student account information only.

Additional synchronization of course enrollments, attendance records, examination results, grades, progress reports, fee information, or other academic data is **not included** within the current scope and may require additional development.

### Data Flow Between Systems

**ERPNext manages:**
- Student records
- Admissions
- Fees and payments
- Branch management
- Administrative operations

**Moodle manages:**
- Course materials
- Assignments
- Examinations
- Student attendance
- Student learning progress
- Live classes

This separation allows each platform to focus on its core functions while reducing system complexity and improving long-term maintainability.

> Integration functionality is limited to the scope explicitly defined in this proposal.

---

## Server Setup & Configuration

- ERPNext Server Setup
  - Installation and configuration on a dedicated Ubuntu server
  - Performance optimization and security hardening
  - Database setup and tuning for scalability

---

## Feature Feasibility Analysis

### Fully Possible Out-of-the-Box (No Custom Development)

| Feature | ERPNext Module |
|---|---|
| Student records (personal details, parent contacts, admission details) | Education module |
| Course & subject enrollment | Education module (Program, Course, Student Enrollment) |
| Fee structure management (subject-wise fees, combo packages) | Education module (Fee Structure, Fee Category) |
| Monthly fee generation & invoicing | Education module (Fee Schedule) |
| Fee collection & payment tracking (cash, bank, digital) | Accounting module (Payment Entry) |
| Fee pending & defaulter tracking | Built-in reports (Sales Invoice outstanding, Dunning) |
| Multi-branch management | Branch master + branch-wise filtering |
| Staff & employee database | HR module (Employee master, documents) |
| Staff attendance | HR module (Employee Checkin, Attendance) |
| Leave management (requests, approvals, balance) | HR module (Leave Application, Leave Policy) |
| Payroll management (salary structure, monthly processing, salary slips) | Payroll module |
| Role-based access (Super Admin, Branch Admin, Staff) | Frappe permission system |
| CRM (leads, follow-ups, conversion to admission) | CRM module (Lead, Opportunity) |
| Document management (attached to any record) | File manager |
| Asset management (registration, allocation, maintenance, branch-wise) | Asset module |
| Finance & accounting (AR, AP, GL, P&L, Balance Sheet) | Accounting module |
| Dashboards & reports | Built-in dashboards + Report Builder |
| Payment email notifications | Auto email on Payment Entry + Fee reminders |

### Possible with Configuration Only (No Code)

| Feature | What's Needed |
|---|---|
| Combination packages (Physics + Chemistry = KWD 40) | Create as separate Programs/Courses with combined fee |
| Monthly billing cycles | Configure Fee Schedule with monthly frequency |
| Discount on fees | Fee Structure discount field or Pricing Rule |
| Branch-wise financial reports | Accounting reports filter by Branch dimension |
| Arabic language support | Built-in translations, RTL layout |
| KWD currency | Standard currency in ERPNext |

### Requires Custom Development

| Feature | Effort | Notes |
|---|---|---|
| Biometric attendance integration | Medium | Depends on biometric device API |
| Kuwait-specific payroll (indemnity, GOSI, overtime) | Medium-High | Custom salary components + Python formulas |
| Digital payment gateway (KNET, etc.) | Medium | No native Kuwait gateway plugin; custom integration needed |
| Moodle student sync integration | Medium | Custom app with REST API calls to Moodle |
| Custom defaulter reports (specific format) | Low-Medium | Standard reports exist; custom formatting may need work |
| Custom dashboards (specific KPIs) | Low-Medium | Dashboard Builder exists; specific layouts may need customization |

### Not in Scope (Per Requirements)

| Feature | Reason |
|---|---|
| Automated course enrollment sync to Moodle | Explicitly excluded - manual only |
| Attendance/exam results sync between Moodle & ERPNext | Explicitly excluded |
| Real-time live class integration | Moodle's responsibility |

---

## Project Structure

```
tuition-erp/
├── .gitignore              # Git ignore rules
├── compose.yaml            # Docker Compose configuration (9 services)
├── frappe.conf             # Custom nginx config for frontend
├── nginx-header-fix.conf   # Nginx header buffer settings
└── README.md               # This file
```

## Docker Services

| Service | Image | Purpose |
|---|---|---|
| backend | frappe/erpnext:v15 | Gunicorn web server (port 8000) |
| frontend | frappe/erpnext:v15 | Nginx reverse proxy (port 8080) |
| websocket | frappe/erpnext:v15 | Socket.io server |
| queue-default | frappe/erpnext:v15 | Default queue worker |
| queue-short | frappe/erpnext:v15 | Short queue worker |
| queue-long | frappe/erpnext:v15 | Long queue worker |
| scheduler | frappe/erpnext:v15 | Cron scheduler |
| db | mariadb:10.6 | Database |
| redis | redis:6.2-alpine | Cache + queue backend |

## Useful Commands

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Check status
docker compose ps

# View logs
docker compose logs -f

# Access backend console
docker compose exec backend bench --site erpnext.localhost console

# Run bench commands
docker compose exec backend bench --site erpnext.localhost [command]

# Backup site
docker compose exec backend bench --site erpnext.localhost backup

# Restore site
docker compose exec backend bench --site erpnext.localhost restore /path/to/backup.sql
```

---

## License

This project is deployed using ERPNext which is licensed under GPL-3.0.
