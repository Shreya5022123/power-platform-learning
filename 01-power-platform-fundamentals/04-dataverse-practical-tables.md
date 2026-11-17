# Dataverse Practical - Insurance Claim Management

## 1. Project Overview
Create an Insurance Claim Management data model using Microsoft Dataverse.

Tables:
- Customer
- Insurance Policy
- Insurance Claim

## 2. Customer Table
<img width="2836" height="1338" alt="image" src="https://github.com/user-attachments/assets/81a8138d-7740-480b-af4c-37d165089f48" />

Columns:
- Customer Name (Primary Name)
- Email (Email)
- Phone Number (Phone)
- Date of Birth (Date Only)
- Address (Text)
- Customer Type (Choice: Individual, Corporate)

## 3. Insurance Policy Table
<img width="2940" height="1442" alt="image" src="https://github.com/user-attachments/assets/78a04104-f3b7-43f0-ac0c-733caa92543e" />

Columns:
- Policy Name (Primary Name)
- Policy Number (Autonumber: POL-{SEQNUM:5})
- Policy Type (Choice: Health Insurance, Life Insurance, Term Insurance)
- Premium Amount (Currency)
- Sum Assured (Currency)
- Start Date (Date Only)
- End Date (Date Only)
- Policy Status (Choice: Active, Expired, Cancelled)
- Customer (Lookup: Customer)

Relationship:
Customer 1:N Insurance Policy.

## 4. Insurance Claim Table
<img width="2890" height="1602" alt="image" src="https://github.com/user-attachments/assets/7cb25e2e-cdd3-4acc-8d02-ff8a1e2e5633" />

Columns:
- Claim Name (Primary Name)
- Claim Number (Autonumber: CLM-{SEQNUM:5})
- Claim Amount (Currency)
- Claim Date (Date Only)
- Claim Status (Choice: Submitted, Under Review, Approved, Rejected, Settled)
- Rejection Reason (Multiple Lines of Text)
- Settlement Date (Date Only)
- Description (Multiple Lines of Text)
- Insurance Policy (Lookup: Insurance Policy)

Relationship:
Insurance Policy 1:N Insurance Claim.

## 5. Complete Relationship Structure

Customer 1:N Insurance Policy 1:N Insurance Claim.

- One customer can have multiple policies.
- Each policy belongs to one customer.
- One policy can have multiple claims.
- Each claim belongs to one policy.

## 6. Important Concepts Practised

- Creating Dataverse tables.
- Adding columns and choosing data types.
- Creating Choice columns.
- Creating Autonumber columns.
- Creating Lookup columns.
- Establishing one-to-many relationships.
- Adding sample records.
- Understanding parent and child tables.
