# Microsoft Dataverse Fundamentals

## 1. Definition
Microsoft Dataverse is a cloud-based data platform used to securely store and manage business data in a structured format.

It integrates with Power Platform and provides built-in data management and security capabilities.

## 2. Basic Structure

Dataverse organises information using:

- Tables: Store a particular type of business information.
- Rows: Represent individual records.
- Columns: Represent attributes of records.

Example:
Customer table -> Customer ID, Name, Email, Phone.

## 3. Column Data Types

- Text: Stores textual information.
- Whole Number: Stores integer values.
- Decimal Number: Stores decimal values.
- Currency: Stores monetary values.
- Date and Time: Stores dates and times.
- Yes/No: Stores Boolean values.
- Choice: Stores predefined options.
- Lookup: References a record in another table.
- Image: Stores images.
- File: Stores files.

## 4. Primary Key

Every Dataverse table has a primary key that uniquely identifies each row.

Dataverse typically uses a GUID (Globally Unique Identifier) as its primary key.

Example:
8f12a3b4-1234-4567-89ab-123456789abc

An Auto Number column can generate readable identifiers such as CLM-00001.

Note: An Auto Number column is not the same as the primary key.

## 5. Relationships

### One-to-Many (1:N)
One record in Table A can be associated with multiple records in Table B.

Example: One customer can have multiple policies.

### Many-to-One (N:1)
Multiple records in Table A can be associated with one record in Table B.

Example: Multiple policies can belong to one customer.

### Many-to-Many (N:N)
Multiple records in Table A can be associated with multiple records in Table B.

Example: Employees can work on multiple projects, and projects can have multiple employees.

## 6. Standard vs Custom Tables

Standard Tables:
- Provided by Microsoft or installed applications.
- Examples: Account, Contact, Activity, Business Unit.

Custom Tables:
- Created to meet specific business requirements.
- Examples: Insurance Policy, Insurance Claim, Claim Approval.

Always check whether an existing standard table meets the requirement before creating a custom table.

## 7. Lookup Column

A Lookup column creates a reference to a record in another table.

Example:
The Policy table contains a Customer Lookup column that references the corresponding Customer record.

## 8. Business Rules

Business Rules allow business logic to be configured without traditional programming.

Common actions:
- Set column values.
- Set column requirements.
- Show or hide columns.
- Enable or disable columns.
- Display validation error messages.

Example:
If Claim Status is Rejected, make Rejection Reason mandatory.

## 9. Dataverse Security

Dataverse security controls who can access data and what operations they can perform.

Important concepts:

- Security Roles: Define user permissions.
- Business Units: Organise users and records.
- Teams: Allow groups of users to share access.
- Column-level Security: Restricts access to specific columns.

Common privileges:
Create, Read, Write, Delete, Append, Append To, Assign and Share.

-  Append: Allows attaching this child record to another parent record (e.g., attaching a Note to an Account).
-  Append To: Allows other child records to be attached to this parent record (e.g., allowing an Account to accept Notes).
-  Assign: Transfers full ownership of a record to another user or team.
-  Share: Grants access to a record for another user or team while keeping your own ownership.


## 10. Insurance Claim Data Model

Customer:
Customer ID, Name, Email, Phone.

Policy:
Policy ID, Policy Number, Policy Type, Customer Lookup.

Claim:
Claim ID, Claim Number, Claim Amount, Status, Policy Lookup.

Employee:
Employee ID, Name, Department.

Relationships:
- Customer 1:N Policy.
- Policy 1:N Claim.
- Employee 1:N Claim (assigned employee).

## 11. Key Takeaway

Dataverse provides structured business data storage using tables, rows and columns. Relationships connect tables, business rules apply business logic, and security roles control data access.
