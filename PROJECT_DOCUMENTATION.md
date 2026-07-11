# REG Learning Center - ERPNext Project Documentation

This document provides step-by-step guides for managing the ERPNext system via the web UI.

---

## Table of Contents

- [System Access](#system-access)
- [Branch Management](#branch-management)
  - [Create a New Branch](#create-a-new-branch)
  - [View All Branches](#view-all-branches)
  - [Edit a Branch](#edit-a-branch)
  - [Delete a Branch](#delete-a-branch)
- [Roles & Permissions](#roles--permissions)
  - [Overview of Roles](#overview-of-roles)
  - [View All Roles](#view-all-roles)
  - [Create a New Role](#create-a-new-role)
  - [Assign Role to a User](#assign-role-to-a-user)
  - [Remove Role from a User](#remove-role-from-a-user)
  - [Configure Role Permissions for DocTypes](#configure-role-permissions-for-doctypes)
  - [Super Admin Guide](#super-admin-guide)
  - [Branch Admin Guide](#branch-admin-guide)
  - [Staff Guide](#staff-guide)
- [Company Management](#company-management)
  - [View Company Details](#view-company-details)
  - [Edit Company Address](#edit-company-address)
- [Fiscal Year Management](#fiscal-year-management)
  - [View Fiscal Years](#view-fiscal-years)
  - [Create New Fiscal Year](#create-new-fiscal-year)
- [Cost Center Management](#cost-center-management)
  - [What are Cost Centers](#what-are-cost-centers)
  - [Current Cost Center Structure](#current-cost-center-structure)
  - [View Cost Centers](#view-cost-centers)
  - [Create a New Cost Center](#create-a-new-cost-center)
  - [Edit a Cost Center](#edit-a-cost-center)
  - [Delete a Cost Center](#delete-a-cost-center)
  - [How Cost Centers Work in Transactions](#how-cost-centers-work-in-transactions)
  - [Branch-Wise Profit & Loss Reports](#branch-wise-profit--loss-reports)
- [Print Formats & Letterhead](#print-formats--letterhead)
  - [What are Print Formats & Letterhead](#what-are-print-formats--letterhead)
  - [Current Setup](#current-setup)
  - [View Letterhead](#view-letterhead)
  - [Add Header HTML to Letterhead (Manual UI Step)](#add-header-html-to-letterhead-manual-ui-step)
  - [Upload Logo to Letterhead](#upload-logo-to-letterhead)
  - [View Print Formats](#view-print-formats)
  - [Link Print Format to Letterhead (Manual UI Step)](#link-print-format-to-letterhead-manual-ui-step)
  - [Create a New Print Format](#create-a-new-print-format)
  - [Preview a Print Format](#preview-a-print-format)
- [Number Series](#number-series)
  - [What are Number Series](#what-are-number-series)
  - [Current REG Number Series](#current-reg-number-series)
  - [View Number Series Settings](#view-number-series-settings)
  - [Change Number Series for a DocType](#change-number-series-for-a-doctype)
- [Email Configuration](#email-configuration)
  - [Current Email Setup](#current-email-setup)
  - [View Email Settings](#view-email-settings)
  - [Test Email Sending](#test-email-sending)
  - [Change Email Password](#change-email-password)
  - [Email Signature](#email-signature)
- [Language Management (English & Arabic)](#language-management-english--arabic)
  - [Enable Arabic in System Settings](#enable-arabic-in-system-settings)
  - [Switch User Language to Arabic](#switch-user-language-to-arabic)
  - [Switch Back to English](#switch-back-to-english)
  - [What Changes When Language is Switched](#what-changes-when-language-is-switched)
  - [Troubleshooting Language Issues](#troubleshooting-language-issues)

---

## System Access

- **URL**: `http://localhost:8080`
- **Username**: `Administrator`
- **Password**: `admin`

> **Warning**: Change the default password after first login for production use.

---

## Branch Management

### Create a New Branch

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **Branch** and select **Branch List**
4. Click **+ Add Branch** button (top right)
5. Fill in the form:
   - **Branch Name**: Enter the branch name (e.g., `Salmiya`)
   - **Is Group**: Leave unchecked (only check if it's a parent category for sub-branches)
6. Click **Save** (blue button at top right)
7. The branch is now created and available for use

**Existing Branches:**
- Jaleeb (Head Office)
- Mangaf

---

### View All Branches

1. Login to ERPNext
2. Click the **search bar** at the top
3. Type **Branch** and select **Branch List**
4. You will see a list of all branches:
   - Branch Name
   - Is Group (Yes/No)
5. Click on any branch name to view its details

---

### Edit a Branch

1. Go to **Branch List** (search bar → "Branch" → Branch List)
2. Click on the branch name you want to edit
3. Make your changes to the branch name or other fields
4. Click **Save** (blue button at top right)
5. The changes are saved immediately

**Note**: If the branch is already linked to students, employees, or transactions, changing the branch name will affect all linked records.

---

### Delete a Branch

1. Go to **Branch List** (search bar → "Branch" → Branch List)
2. Click on the branch name you want to delete
3. Click the **three dots menu** (⋯) at the top right
4. Select **Delete**
5. A confirmation dialog will appear
6. Click **Yes** to confirm

**Warning**: 
- You cannot delete a branch that is linked to existing records (students, employees, invoices, etc.)
- To delete a linked branch, you must first remove or reassign all records associated with that branch
- Deletion is permanent and cannot be undone
- Consider disabling instead of deleting if the branch has historical data

**To disable a branch instead of deleting:**
- Currently ERPNext does not have a "disabled" field for branches
- Rename the branch with a prefix like `INACTIVE - Salmiya` to indicate it's no longer active

---

## Roles & Permissions

### Overview of Roles

The system has three custom roles configured for the tuition center:

| Role | Access Level | Description |
|---|---|---|
| **Super Admin** | Full system access | Complete control over all modules, settings, and data. Can create, read, update, delete, submit, and cancel any document. Inherits System Manager capabilities. |
| **Branch Admin** | Branch-level management | Manage students, fees, CRM, HR, and attendance for their assigned branch. Can create, read, write, submit, and cancel documents. Cannot delete records or change system settings. |
| **Staff** | Limited access | Day-to-day operations only. Can view student records, mark attendance, apply for leave, and create leads. Cannot submit or cancel documents. |

**DocType Permissions:**

| DocType | Super Admin | Branch Admin | Staff |
|---|---|---|---|
| Student | Full | Create, Read, Write, Submit, Cancel | Read, Write, Create |
| Student Admission | Full | Create, Read, Write, Submit, Cancel | - |
| Student Enrollment | Full | Create, Read, Write, Submit, Cancel | - |
| Fee Structure | Full | Create, Read, Write, Submit, Cancel | - |
| Fee Schedule | Full | Create, Read, Write, Submit, Cancel | - |
| Fees | Full | Create, Read, Write, Submit, Cancel | - |
| Sales Invoice | Full | Create, Read, Write, Submit, Cancel | - |
| Payment Entry | Full | Create, Read, Write, Submit, Cancel | - |
| Lead | Full | Create, Read, Write, Submit, Cancel | Read, Write, Create |
| Opportunity | Full | Create, Read, Write, Submit, Cancel | - |
| Employee | Full | Create, Read, Write, Submit, Cancel | - |
| Attendance | Full | Create, Read, Write, Submit, Cancel | Read, Write, Create |
| Leave Application | Full | Create, Read, Write, Submit, Cancel | Read, Write, Create |
| Student Attendance | Full | Create, Read, Write, Submit, Cancel | Read, Write, Create |
| Branch | Full | Create, Read, Write, Submit, Cancel | - |

---

### View All Roles

1. Login to ERPNext
2. Click the **search bar** at the top
3. Type **Role** and select **Role List**
4. You will see all 52 roles (49 built-in + 3 custom):
   - Super Admin
   - Branch Admin
   - Staff
   - (plus 49 built-in roles like Accounts Manager, HR Manager, etc.)
5. Click on any role name to view its details

---

### Create a New Role

1. Go to **Role List** (search bar → "Role" → Role List)
2. Click **+ Add Role** button (top right)
3. Fill in the form:
   - **Role Name**: Enter the role name (e.g., `Accountant`)
   - **Desk Access**: Check this box if the role needs access to the desktop interface
   - **Disabled**: Leave unchecked
4. Click **Save**
5. The role is created but has no permissions yet - you need to configure permissions separately

---

### Assign Role to a User

1. Click the **search bar** at the top
2. Type **User** and select **User List**
3. Click on the user you want to assign a role to
4. Scroll down to the **Roles** section
5. Check the checkbox next to the role(s) you want to assign:
   - [x] Super Admin
   - [x] Branch Admin
   - [x] Staff
6. Click **Save** (blue button at top right)
7. The user now has the assigned role(s) and corresponding permissions

**Note**: A user can have multiple roles. The permissions are combined (union of all role permissions).

---

### Remove Role from a User

1. Go to **User List** (search bar → "User" → User List)
2. Click on the user you want to modify
3. Scroll down to the **Roles** section
4. Uncheck the checkbox next to the role you want to remove
5. Click **Save**
6. The user no longer has that role's permissions

---

### Configure Role Permissions for DocTypes

1. Click the **search bar** at the top
2. Type **Role Permissions Manager** and select it
3. Select the **DocType** from the dropdown (e.g., "Student")
4. You will see a table showing all roles and their permission levels for that DocType
5. To modify permissions:
   - Check/uncheck boxes for: Read, Write, Create, Delete, Submit, Cancel, Amend
   - Set **Permission Level** if needed (0 = default, higher levels for field-level permissions)
6. Click **Save** or changes are saved automatically

**Permission Levels:**
- **Level 0**: Default document-level access
- **Level 1-9**: Field-level permissions (for restricting specific fields)

**To add a new role to a DocType:**
1. Open Role Permissions Manager
2. Select the DocType
3. Click **Add New Role** button
4. Select the role from the dropdown
5. Set the permission checkboxes
6. Save

---

### Super Admin Guide

**Who should have this role**: Institute owner, principal, or top-level management

**Capabilities:**
- Full access to all modules and features
- Can create, edit, delete any record
- Can change system settings
- Can manage users and roles
- Can view all branches' data
- Can submit and cancel any document
- Can configure fee structures, payroll, and accounting

**How to use:**
1. Login with a user account that has the Super Admin role
2. All modules and workspaces will be visible
3. All actions (create, edit, delete, submit, cancel) are available on every document
4. Settings menu is accessible for system configuration

**Recommended for**: 1-2 users only (Institute Director, IT Administrator)

---

### Branch Admin Guide

**Who should have this role**: Branch coordinator or branch manager

**Capabilities:**
- Manage students at their branch (create, edit, enroll)
- Manage fee collection and payments
- Handle CRM leads and admissions
- Manage staff attendance and leave approvals
- View branch-wise reports
- Cannot delete records
- Cannot change system settings
- Cannot manage users or roles

**How to use:**
1. Login with a user account that has the Branch Admin role
2. You will see modules: Education, CRM, Accounting, HR, Attendance
3. You can create and manage:
   - Student records → search "Student" → Add Student
   - Fee collection → search "Fees" → Create Fees
   - Leads → search "Lead" → Add Lead
   - Attendance → search "Attendance" → Mark Attendance
4. You can submit and cancel documents (e.g., submit a fee receipt)
5. You cannot delete records - contact Super Admin for deletions

**Recommended for**: 1 user per branch (Branch Manager/Coordinator)

---

### Staff Guide

**Who should have this role**: Teachers, administrative staff, receptionists

**Capabilities:**
- View student records (read-only for most fields)
- Mark student attendance
- Mark their own attendance
- Apply for leave
- Create leads (enquiries from parents)
- Cannot submit or cancel documents
- Cannot manage fees, payroll, or settings

**How to use:**
1. Login with a user account that has the Staff role
2. You will see limited modules: Education (students), Attendance
3. You can:
   - View students → search "Student" → click to view (read-only)
   - Mark attendance → search "Student Attendance" → Add Student Attendance
   - Apply for leave → search "Leave Application" → Add Leave Application
   - Create leads → search "Lead" → Add Lead
4. You cannot submit or cancel documents
5. You cannot access fees, payroll, or accounting modules

**Recommended for**: All teaching and administrative staff

---

## Company Management

### View Company Details

1. Login to ERPNext
2. Click the **search bar**
3. Type **Company** and select **Company List**
4. Click on **REG Learning Center**
5. You will see:
   - Company Name: REG Learning Center
   - Abbreviation: REG
   - Country: Kuwait
   - Default Currency: KWD
   - Domain: Education
   - Chart of Accounts (auto-generated)

---

### Edit Company Address

1. Go to **Company List** → click **REG Learning Center**
2. Scroll down to the **Address & Contact** section
3. Click on the address record (REG Learning Center-Office)
4. Edit the address fields as needed
5. Click **Save**

**Current Address:**
- Floor No. 1, Building No. 172
- Street 25, Block 4
- Jaleeb Al Shuyoukh, Kuwait
- Phone: 65546684

---

## Fiscal Year Management

### View Fiscal Years

1. Click the **search bar**
2. Type **Fiscal Year** and select **Fiscal Year List**
3. You will see:
   - 2025-2026 (Jul 1, 2025 → Jun 30, 2026) - Active

---

### Create New Fiscal Year

1. Go to **Fiscal Year List** (search bar → "Fiscal Year" → Fiscal Year List)
2. Click **+ Add Fiscal Year**
3. Fill in:
   - **Year**: e.g., `2026-2027`
   - **Year Start Date**: `2026-07-01`
   - **Year End Date**: `2027-06-30`
4. In the **Companies** table, add REG Learning Center
5. Click **Save**

**Note**: Fiscal years cannot overlap for the same company. Ensure dates don't conflict with existing fiscal years.

---

## Cost Center Management

### What are Cost Centers

Cost centers are a way to **track income and expenses by branch**. They allow you to see profit/loss for each branch separately.

**Without cost centers:**
```
REG Learning Center (total)
  ├── Income: 5,000 KWD
  └── Expenses: 3,000 KWD
  └── Profit: 2,000 KWD
```

**With cost centers:**
```
REG Learning Center (total)
  ├── Jaleeb Branch
  │   ├── Income: 3,000 KWD (fees collected)
  │   ├── Expenses: 1,800 KWD (rent, salary, utilities)
  │   └── Profit: 1,200 KWD
  │
  ├── Mangaf Branch
  │   ├── Income: 2,000 KWD (fees collected)
  │   ├── Expenses: 1,200 KWD (rent, salary, utilities)
  │   └── Profit: 800 KWD
```

### Current Cost Center Structure

```
REG Learning Center - REG (Root, Group)
├── Main - REG (default)
├── Jaleeb Branch - REG (Group)
│   ├── Jaleeb - Income - REG
│   └── Jaleeb - Expenses - REG
└── Mangaf Branch - REG (Group)
    ├── Mangaf - Income - REG
    └── Mangaf - Expenses - REG
```

**Total: 8 cost centers**

| Cost Center | Type | Purpose |
|---|---|---|
| REG Learning Center - REG | Group (Root) | Parent for all cost centers |
| Main - REG | Non-Group | Default cost center for untagged transactions |
| Jaleeb Branch - REG | Group | Parent for Jaleeb sub-cost centers |
| Jaleeb - Income - REG | Non-Group | Tag fee income from Jaleeb branch |
| Jaleeb - Expenses - REG | Non-Group | Tag expenses (rent, salary) for Jaleeb branch |
| Mangaf Branch - REG | Group | Parent for Mangaf sub-cost centers |
| Mangaf - Income - REG | Non-Group | Tag fee income from Mangaf branch |
| Mangaf - Expenses - REG | Non-Group | Tag expenses (rent, salary) for Mangaf branch |

---

### View Cost Centers

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **Cost Center** and select **Cost Center List**
4. You will see a tree view showing:
   - REG Learning Center (root)
     - Main
     - Jaleeb Branch
       - Jaleeb - Income
       - Jaleeb - Expenses
     - Mangaf Branch
       - Mangaf - Income
       - Mangaf - Expenses

**Alternative**: Search **Chart of Cost Centers** to see the tree structure visually.

---

### Create a New Cost Center

1. Go to **Cost Center List** (search bar → "Cost Center" → Cost Center List)
2. Click **+ Add Cost Center** button (top right)
3. Fill in the form:
   - **Cost Center Name**: e.g., `Salmiya Branch`
   - **Parent Cost Center**: Select `REG Learning Center - REG` (for a new branch)
   - **Is Group**: Check this if you want to add sub-cost centers under it
   - **Company**: REG Learning Center (auto-filled)
4. Click **Save**

**To add sub-cost centers (Income/Expenses):**
1. Create the branch as a **Group** cost center first
2. Then create Income and Expenses as non-group cost centers under it
3. Set Parent Cost Center = the branch name

**Example for a new branch:**
```
1. Create "Salmiya Branch" (Group, parent: REG Learning Center - REG)
2. Create "Salmiya - Income" (Non-Group, parent: Salmiya Branch - REG)
3. Create "Salmiya - Expenses" (Non-Group, parent: Salmiya Branch - REG)
```

---

### Edit a Cost Center

1. Go to **Cost Center List** (search bar → "Cost Center" → Cost Center List)
2. Click on the cost center name you want to edit
3. Make your changes (name, parent, etc.)
4. Click **Save**

**Note**: Changing the parent cost center will move the entire sub-tree. Be cautious with cost centers that have existing transactions.

---

### Delete a Cost Center

1. Go to **Cost Center List**
2. Click on the cost center name you want to delete
3. Click the **three dots menu** (⋯) at the top right
4. Select **Delete**
5. Confirm by clicking **Yes**

**Warning**:
- You **cannot delete** a cost center that has linked transactions (invoices, payments, journal entries)
- You **cannot delete** a Group cost center that has child cost centers
- Delete child cost centers first, then the parent
- Consider renaming to `INACTIVE - name` instead of deleting if it has historical data

---

### How Cost Centers Work in Transactions

When creating any financial transaction, you can tag it with a cost center:

**Fee Collection (Sales Invoice):**
1. Search **Sales Invoice** → click **+ Add Sales Invoice**
2. Fill in student details and fee amount
3. Look for the **Cost Center** field (usually in the accounting section)
4. Select the appropriate branch cost center:
   - `Jaleeb - Income - REG` for Jaleeb branch fees
   - `Mangaf - Income - REG` for Mangaf branch fees
5. Save and submit the invoice

**Expense Recording (Journal Entry / Payment Entry):**
1. Search **Journal Entry** → click **+ Add Journal Entry**
2. Enter the expense details
3. Select the appropriate branch expense cost center:
   - `Jaleeb - Expenses - REG` for Jaleeb branch expenses
   - `Mangaf - Expenses - REG` for Mangaf branch expenses
4. Save and submit

**Salary Processing (Salary Slip):**
1. When processing payroll, tag each salary slip with the employee's branch cost center
2. This automatically tracks salary expenses per branch

---

### Branch-Wise Profit & Loss Reports

1. Search **Profit and Loss Statement**
2. Open the report
3. Set filters:
   - **Company**: REG Learning Center
   - **From Date**: Start of fiscal year
   - **To Date**: End date for report
   - **Cost Center**: Select a specific branch (e.g., `Jaleeb Branch - REG`)
4. Click **Report** to generate
5. You will see income and expenses only for that branch
6. Repeat with `Mangaf Branch - REG` to compare

**To see all branches at once:**
1. Open **Profit and Loss Statement**
2. Leave Cost Center blank (shows all)
3. Or use the **Consolidated P&L** report
4. Use **Dimension Filters** to break down by cost center

**Other useful reports:**
- **Trial Balance**: Filter by cost center to see account balances per branch
- **Balance Sheet**: Can be filtered by cost center
- **General Ledger**: Filter by cost center for detailed transactions

---

## Print Formats & Letterhead

### What are Print Formats & Letterhead

**Letterhead** is the header and footer that appears on every printed document (fee receipts, invoices, letters). It contains the institute name, logo, address, and contact info.

**Print Format** is the layout and design of the document content itself (what fields appear, how they're arranged, styling).

```
┌─────────────────────────────────────────────┐
│  [LOGO]  REG Learning Center               │  ← Letterhead (header)
│          Jaleeb Al Shuyoukh, Kuwait         │
│          Tel: 65546684                      │
├─────────────────────────────────────────────┤
│                                             │
│         FEE RECEIPT                         │  ← Print Format (content)
│         Receipt No: INV-001                 │
│         Student: Ahmed Ali                  │
│         Amount: 150.000 KWD                 │
│                                             │
├─────────────────────────────────────────────┤
│  REG Learning Center | www.reg.edu.kw      │  ← Letterhead (footer)
└─────────────────────────────────────────────┘
```

### Current Setup

| Item | Name | Type | Status |
|---|---|---|---|
| Letterhead | REG Learning Center | Default letterhead | Created (footer configured, header needs manual step) |
| Print Format | Fee Receipt | Sales Invoice (Jinja/HTML) | Created (2,145 chars HTML) |
| Print Format | REG Standard Invoice | Sales Invoice (Jinja/HTML) | Created (2,913 chars HTML) |

---

### View Letterhead

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **Letter Head** and select **Letter Head List**
4. Click on **REG Learning Center**
5. You will see:
   - Letter Head Name: REG Learning Center
   - Is Default: Checked
   - Header: (HTML editor - needs content)
   - Footer: HTML with institute info

---

### Add Header HTML to Letterhead (Manual UI Step)

The letterhead header could not be set via API. You need to add it manually:

1. Go to **Letter Head List** → click **REG Learning Center**
2. Find the **Header** field (HTML editor area)
3. Click the **HTML/source code** button (or click in the editor area)
4. Paste the following HTML:

```html
<div style="text-align: center;">
  <h2 style="margin: 0; color: #1a4f8b;">REG Learning Center</h2>
  <p style="margin: 2px 0; font-size: 12px; color: #555;">
    Floor No. 1, Building No. 172, Street 25, Block 4, Jaleeb Al Shuyoukh, Kuwait
  </p>
  <p style="margin: 2px 0; font-size: 12px; color: #555;">
    Tel: 65546684 | Email: info@reg.edu.kw
  </p>
  <hr style="border: 1px solid #1a4f8b; margin: 5px 0;">
</div>
```

5. Click **Save**

---

### Upload Logo to Letterhead

To add the institute logo to the letterhead:

1. Go to **Letter Head List** → click **REG Learning Center**
2. In the **Header** field, click the image upload icon in the HTML editor
3. Upload the REG Learning Center logo image (PNG/JPG, recommended size: 200x60px)
4. Position the logo as desired (left, center, or right)
5. Click **Save**

**Logo tips:**
- Use a transparent PNG for best results
- Recommended dimensions: 200x60 pixels or similar
- Keep file size under 100KB for fast printing

---

### View Print Formats

1. Click the **search bar** at the top
2. Type **Print Format** and select **Print Format List**
3. You will see:
   - **Fee Receipt** (for Sales Invoice)
   - **REG Standard Invoice** (for Sales Invoice)
   - Plus any built-in ERPNext print formats
4. Click on any format name to view/edit its HTML

---

### Link Print Format to Letterhead (Manual UI Step)

The print formats need to be linked to the letterhead manually:

1. Go to **Print Format List** → click **Fee Receipt**
2. Find the **Letter Head** field
3. Select **REG Learning Center** from the dropdown
4. Click **Save**
5. Repeat for **REG Standard Invoice**

---

### Create a New Print Format

1. Go to **Print Format List** (search bar → "Print Format" → Print Format List)
2. Click **+ Add Print Format**
3. Fill in:
   - **Print Format Name**: e.g., `Student ID Card`
   - **Doc Type**: Select the document type (e.g., "Student")
   - **Print Format Type**: Select "Jinja" for custom HTML or "Standard" for default layout
   - **Letter Head**: Select "REG Learning Center"
4. If Jinja type, write HTML template in the **HTML** field
5. Click **Save**

---

### Preview a Print Format

1. Open any document (e.g., a Sales Invoice)
2. Click the **Print icon** (printer icon at top right)
3. Select the print format from the dropdown (e.g., "Fee Receipt")
4. The document will display with the selected format and letterhead
5. Click **Print** or **PDF** to export

---

## Number Series

### What are Number Series

Number series automatically generate sequential numbers for documents (invoices, receipts, student IDs, etc.). They ensure each document has a unique, traceable identifier.

**Example:**
```
First Sales Invoice:  REG-INV-2025-0001
Second Sales Invoice: REG-INV-2025-0002
Third Sales Invoice:  REG-INV-2025-0003
```

### Current REG Number Series

All number series use the **REG** prefix with year-based numbering:

| DocType | Number Series | Example |
|---|---|---|
| Sales Invoice | `REG-INV-.YYYY.-` | REG-INV-2025-0001 |
| Payment Entry | `REG-PAY-.YYYY.-` | REG-PAY-2025-0001 |
| Journal Entry | `REG-JV-.YYYY.-` | REG-JV-2025-0001 |
| Sales Order | `REG-SO-.YYYY.-` | REG-SO-2025-0001 |
| Customer | `REG-CUST-.YYYY.-` | REG-CUST-2025-0001 |
| Supplier | `REG-SUPP-.YYYY.-` | REG-SUPP-2025-0001 |
| Quotation | `REG-QUO-.YYYY.-` | REG-QUO-2025-0001 |
| Purchase Order | `REG-PO-.YYYY.-` | REG-PO-2025-0001 |
| Purchase Invoice | `REG-PINV-.YYYY.-` | REG-PINV-2025-0001 |
| Stock Entry | `REG-STE-.YYYY.-` | REG-STE-2025-0001 |
| Delivery Note | `REG-DN-.YYYY.-` | REG-DN-2025-0001 |
| Material Request | `REG-MR-.YYYY.-` | REG-MR-2025-0001 |
| Employee | `REG-EMP-.YYYY.-` | REG-EMP-2025-0001 |
| Lead | `REG-LEAD-.YYYY.-` | REG-LEAD-2025-0001 |
| Opportunity | `REG-OPP-.YYYY.-` | REG-OPP-2025-0001 |

**Additional series created (for Education module - will be linked when module is installed):**

| DocType | Number Series | Example |
|---|---|---|
| Student | `REG-STU-.YYYY.-` | REG-STU-2025-0001 |
| Student Applicant | `REG-APP-.YYYY.-` | REG-APP-2025-0001 |
| Student Group | `REG-SG-.YYYY.-` | REG-SG-2025-0001 |
| Program Enrollment | `REG-PE-.YYYY.-` | REG-PE-2025-0001 |
| Fee Structure | `REG-FS-.YYYY.-` | REG-FS-2025-0001 |
| Fee Schedule | `REG-FSC-.YYYY.-` | REG-FSC-2025-0001 |
| Fees | `REG-FEE-.YYYY.-` | REG-FEE-2025-0001 |
| Salary Slip | `REG-SS-.YYYY.-` | REG-SS-2025-0001 |
| Leave Application | `REG-LA-.YYYY.-` | REG-LA-2025-0001 |
| Attendance | `REG-ATT-.YYYY.-` | REG-ATT-2025-0001 |
| Payroll Entry | `REG-PR-.YYYY.-` | REG-PR-2025-0001 |

**Total: 26 number series created, 15 doctypes currently configured**

---

### View Number Series Settings

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **Customize Form** and select it
4. Select the DocType you want to check (e.g., "Sales Invoice")
5. Look for the **Naming Series** field
6. You will see `REG-INV-.YYYY.-` as the available option

**Alternative**: Open any document (e.g., Sales Invoice) → look at the **Naming Series** field at the top of the form.

---

### Change Number Series for a DocType

1. Search **Customize Form** → open it
2. Select **Doc Type** (e.g., "Sales Invoice")
3. Find the **Naming Series** field
4. You can:
   - **Add multiple series**: Enter each on a new line (e.g., add `REG-INV-OLD-.YYYY.-` for legacy invoices)
   - **Change default**: The first series in the list is the default
5. Click **Save**
6. New documents will use the selected naming series

**Note**: Existing documents keep their original numbers. Only new documents use the updated series.

---

## Email Configuration

### Current Email Setup

| Setting | Value |
|---|---|
| Email Address | info@abijithcb.com |
| Account Name | REG Learning Center |
| Service | Gmail |
| SMTP Server | smtp.gmail.com |
| SMTP Port | 587 |
| TLS | Enabled |
| SSL | Disabled |
| Outgoing | Enabled (Default) |
| Incoming | Disabled |
| Signature | Enabled (REG Learning Center footer) |
| Email Domain | abijithcb.com |

The system sends emails (fee receipts, invoices, notifications, password resets) via this Gmail account using an App Password.

---

### View Email Settings

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **Email Account** and select **Email Account List**
4. Click on **REG Learning Center** (or info@abijithcb.com)
5. You will see:
   - Email Address: info@abijithcb.com
   - Outgoing: Enabled
   - Default Outgoing: Enabled
   - SMTP Server: smtp.gmail.com
   - Port: 587
   - TLS: Checked
   - Signature: REG Learning Center footer

**To view Email Domain:**
1. Search **Email Domain** → click **Email Domain List**
2. Click on **abijithcb.com**
3. View SMTP settings

---

### Test Email Sending

1. Search **Email Account** → click **REG Learning Center**
2. Click the **three dots menu** (⋯) at the top right
3. Select **Test Notification**
4. A test email will be sent to the Administrator's email
5. Check the inbox to confirm email is working

**Alternative test:**
1. Search **Email Queue** → click **Email Queue List**
2. Any pending/failed emails will show here
3. You can retry failed emails from this page

---

### Change Email Password

If the Gmail App Password needs to be updated:

1. Search **Email Account** → click **REG Learning Center**
2. Find the **Password** field
3. Enter the new App Password
4. Click **Save**

**Note**: This uses a Gmail App Password (not your regular Gmail password). To generate a new App Password:
1. Go to your Google Account settings
2. Security → 2-Step Verification → App Passwords
3. Generate a new password for "Mail"
4. Use that 16-character password in ERPNext

---

### Email Signature

The email signature appears at the bottom of all outgoing emails:

1. Search **Email Account** → click **REG Learning Center**
2. Scroll to the **Signature** section
3. **Add Signature**: Checked
4. **Signature** field contains:
   ```
   REG Learning Center | Jaleeb Al Shuyoukh, Kuwait | Tel: 65546684
   ```
5. Edit as needed and click **Save**

---

## Language Management (English & Arabic)

The system supports both **English** and **Arabic (العربية)** languages. Both are available in the system. Arabic includes automatic RTL (Right-to-Left) layout support.

### Enable Arabic in System Settings

Before users can switch to Arabic, it must be enabled in System Settings:

1. Login to ERPNext at `http://localhost:8080`
2. Click the **search bar** at the top
3. Type **System Settings** and select it
4. Scroll through the settings page to find the **Language** section
5. Look for the **Enabled Languages** field
6. Click in the field and type `ar`
7. You should see **Arabic (العربية)** appear in the dropdown
8. Click to select it
9. Both `en` (English) and `ar` (Arabic) should now be listed in the field
10. Click **Save** button at the top right

**Note**: If you cannot find the Enabled Languages field, try these alternatives:
- Search bar → type **System Settings** → look for tabs at the top of the page
- The field may be under a tab called **Localization** or **General**
- If the field is empty, it means all languages are enabled by default

---

### Switch User Language to Arabic

Once Arabic is enabled in System Settings, each user can switch their language:

1. Click your **profile picture** (top right corner of the screen)
2. Click **Settings** from the dropdown menu
3. Find the **Language** field
4. Click the dropdown and select **Arabic (العربية)**
5. Click **Save**
6. The page will reload automatically
7. The entire UI will now display in Arabic with RTL (Right-to-Left) layout

**What happens:**
- All menus, buttons, labels, and system text switch to Arabic
- The layout flips to Right-to-Left (RTL)
- The sidebar moves to the right side
- Data you entered (student names, fee amounts, etc.) remains unchanged
- Only the system interface language changes

---

### Switch Back to English

1. Click your **profile picture** (top right - now on the right side in RTL mode)
2. Click **الإعدادات** (Settings in Arabic)
3. Find **اللغة** (Language field)
4. Change it back to **English**
5. Click **حفظ** (Save button)
6. The page will reload in English with LTR (Left-to-Right) layout

---

### What Changes When Language is Switched

| Area | English Mode | Arabic Mode |
|---|---|---|
| **UI Labels** | Student, Fee, Invoice, etc. | طالب، رسوم، فاتورة، etc. |
| **Menu Items** | English menu names | Arabic translated menu names |
| **Buttons** | Save, Cancel, Delete | حفظ، إلغاء، حذف |
| **Layout Direction** | Left-to-Right (LTR) | Right-to-Left (RTL) |
| **Sidebar Position** | Left side | Right side |
| **Date Format** | English format | Arabic format |
| **System Messages** | English notifications | Arabic notifications |
| **Your Data** | Unchanged | Unchanged (data stays as entered) |
| **Reports** | English headers | Arabic headers |
| **Print Formats** | English templates | Arabic templates (if translated) |

**Important**: 
- Data you entered (student names, fee amounts, phone numbers, addresses) does **NOT** change
- Only the system interface (menus, labels, buttons) switches language
- Different users can use different languages simultaneously
- The system default language remains English unless changed in System Settings

---

### Troubleshooting Language Issues

**Problem: Language doesn't change after selecting Arabic**

1. **Check if Arabic is enabled in System Settings:**
   - Search bar → System Settings → look for Enabled Languages
   - Make sure `ar` is listed
   - If not, add it and Save

2. **Clear browser cache:**
   - Press `Ctrl + Shift + Delete` in your browser
   - Clear cache and cookies
   - Reload `http://localhost:8080`
   - Login again and try switching language

3. **Hard refresh the page:**
   - Press `Ctrl + F5` (or `Ctrl + Shift + R`)
   - This forces the browser to reload all resources

4. **Check user language setting:**
   - Profile → Settings → Language
   - Make sure it shows Arabic (العربية)
   - If it reverts to English, the System Settings may not have Arabic enabled

5. **Try setting language via URL:**
   - Go to `http://localhost:8080/app/settings`
   - Change Language to Arabic
   - Save and reload

**Problem: Some text still shows in English after switching to Arabic**

- This is normal - not all text is translated in ERPNext
- Core modules (Education, Accounting, HR) are well-translated
- Some custom fields or less common labels may remain in English
- Custom field labels you create will need manual Arabic translations

**Problem: RTL layout looks broken**

1. Hard refresh: `Ctrl + F5`
2. Clear browser cache
3. Try a different browser (Chrome, Firefox, Edge)
4. Make sure you're using the latest browser version

---

## Quick Reference

| Action | Search Term | Path |
|---|---|---|
| View branches | Branch | Branch List |
| View roles | Role | Role List |
| View users | User | User List |
| View company | Company | Company List |
| View fiscal year | Fiscal Year | Fiscal Year List |
| View cost centers | Cost Center | Cost Center List |
| Cost center tree | Chart of Cost Centers | Chart of Cost Centers |
| Profit & Loss by branch | Profit and Loss Statement | Profit and Loss Statement → filter by Cost Center |
| View letterhead | Letter Head | Letter Head List |
| View print formats | Print Format | Print Format List |
| View number series | Customize Form | Customize Form → select DocType → Naming Series |
| View email settings | Email Account | Email Account List |
| View email domain | Email Domain | Email Domain List |
| Email queue | Email Queue | Email Queue List |
| Role permissions | Role Permissions Manager | Role Permissions Manager |
| System settings | System Settings | System Settings |
| Global defaults | Global Defaults | Global Defaults |
| Change language | Settings | Profile → Settings → Language |
| Enable languages | System Settings | System Settings → Enabled Languages |

---

## Tips

- **Search bar** is your best friend - type any document name to find it
- **Keyboard shortcut**: `Ctrl+K` opens the search bar
- **Recent items**: Click the clock icon in the search bar to see recently viewed documents
- **Notifications**: Click the bell icon at the top right for system notifications
- **All workspaces**: Click the grid icon (top left) to see all available modules/workspaces
