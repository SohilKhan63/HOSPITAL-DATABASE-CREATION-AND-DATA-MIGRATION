# HOSPITAL-DATABASE-CREATION-AND-DATA-MIGRATION
Hospital Database Migration &amp; Automation: Migrated Excel-based hospital records to a robust SQL Server database, enforcing data integrity, preventing scheduling conflicts, and enabling department-wise revenue reporting. Built triggers, constraints, and stored procedures to automate appointments and billing.



# Hospital Database Migration & Automation

Project Overview
The Hospital Database Migration & Automation project addresses the inefficiencies and risks associated with maintaining hospital records in Excel. As the hospital scaled, the existing Excel-based system became error-prone, lacked enforceable relationships between data entities, and was difficult to manage.

This project involves designing and implementing a robust relational database system that ensures data integrity, automates critical business rules, and enables actionable reporting. The database captures all core functionalities, including:

Patient management
Doctor rosters and schedules
Appointments
Prescriptions
Lab reports
Billing
Additionally, the project includes migrating existing Excel-based data into the new database while enforcing data consistency and integrity.

# Problem Statement
1. The hospital’s previous system faced several challenges:
2. Lack of Unique Identifiers
Patients, doctors, departments, and appointments did not have guaranteed unique IDs.

This project introduces primary keys and auto-incremented IDs to ensure uniqueness.

# Disconnected Relationships
Appointments were not linked to valid patients or doctors.
The new design enforces referential integrity through foreign keys connecting appointments, patients, doctors, and departments.

# Invalid or Ambiguous Data
1. Examples include inconsistent gender entries, ambiguous appointment statuses, and irregular date formats.
2. Data was cleaned during migration, and constraints/checks were implemented to ensure valid entries.
Unregulated Scheduling
3. Doctors were occasionally double-booked, and appointments were sometimes scheduled in the past.
4. Triggers and constraints prevent invalid appointments and enforce scheduling rules.

# Disconnected Reporting
Billing summaries and department-wise reports were impossible in Excel.
The database supports automated monthly revenue reports by department, integrating billing and appointment data.

# Database Design
The relational database design follows best practices for normalization, referential integrity, and business logic enforcement.

# Key Tables

Patients
Stores patient details with a unique PATIENT_ID.

Doctors
Stores doctor details with a unique DOCTOR_ID.
Linked to departments to manage rosters.

Departments
Stores hospital departments with a unique DEPARTMENT_ID.

Appointments
Links patients to doctors and departments.
STATUS column controlled via a CHECK constraint.
Prevents scheduling in the past or double-booking using triggers.

Prescriptions
Stores medicines prescribed per appointment.

Lab Reports
Stores results linked to appointments/patients.

Bills
Stores billing information for each appointment.
Linked to patients and appointments to allow department-wise revenue aggregation.

Data Migration
Excel Data Cleaning: Removed duplicates, standardized gender and status fields, corrected date formats.
Importing Data: Data was migrated using ETL pipelines, ensuring referential integrity.
Constraints: Primary keys, foreign keys, and check constraints were enforced during import.

# Business Rules Implemented
Unique Identifiers
All major entities have auto-generated primary keys to ensure uniqueness.
Referential Integrity
Foreign key relationships ensure that appointments, bills, and lab reports cannot reference non-existent patients or doctors.
Data Validation
CHECK constraints enforce valid STATUS, GENDER, and other enumerated values.
Appointment Scheduling Rules

# Triggers prevent:
Appointments in the past
Double-booking of doctors

# Revenue Reporting
Stored procedures calculate monthly revenue by department for billing and management reporting.
Sample Queries & Procedures
Insert a new appointment (prevents past scheduling and double-booking)
Generate monthly revenue report by department
Fetch all patients for a specific doctor
List unpaid bills for the month

# Tools & Technologies
Database: SQL Server
Scripting: T-SQL (Triggers, Stored Procedures)
Data Migration: Excel → SQL Server (ETL scripts)
Validation: Constraints, CHECK, and triggers for business rules

# Achievements
1. Successfully migrated existing Excel data while enforcing integrity.
2. Implemented preventive measures for double-booking and past appointments.
3. Enabled department-wise monthly revenue reporting.
4. Built a scalable and maintainable hospital database that improves operational efficiency and reduces errors.

# Future Work
1. Implement role-based access control for doctors, lab technicians, and billing staff.
2. Extend reporting capabilities to yearly and quarterly revenue analytics.
3. Build a front-end dashboard to interact with the database for hospital staff.
