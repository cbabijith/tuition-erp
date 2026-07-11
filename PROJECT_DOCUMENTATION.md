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

## Quick Reference

| Action | Search Term | Path |
|---|---|---|
| View branches | Branch | Branch List |
| View roles | Role | Role List |
| View users | User | User List |
| View company | Company | Company List |
| View fiscal year | Fiscal Year | Fiscal Year List |
| Role permissions | Role Permissions Manager | Role Permissions Manager |
| System settings | System Settings | System Settings |
| Global defaults | Global Defaults | Global Defaults |

---

## Tips

- **Search bar** is your best friend - type any document name to find it
- **Keyboard shortcut**: `Ctrl+K` opens the search bar
- **Recent items**: Click the clock icon in the search bar to see recently viewed documents
- **Notifications**: Click the bell icon at the top right for system notifications
- **All workspaces**: Click the grid icon (top left) to see all available modules/workspaces
