# 05 - Dataverse Forms and Views

## 1. Forms

Forms provide the user interface for creating, viewing and editing individual Dataverse records.

### Types of Forms

- Main Form: Used to create, view and edit complete records.
- Quick Create Form: Allows users to create records quickly with fewer fields.
- Quick View Form: Displays information from a related record within another form.
- Card Form: Displays compact record information.

### Example

An Insurance Claim Main Form can contain:

- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy (Lookup)
- Rejection Reason
- Settlement Date
- Description

## 2. Views

Views display multiple Dataverse records in a list.

A view defines:
- Which columns are displayed.
- Which records are included using filters.
- How records are sorted.
- The order of displayed columns.

### Example Views for Insurance Claims

- All Claims: Displays all claim records.
- Pending Claims: Displays claims with Submitted or Under Review status.
- Approved Claims: Displays claims with Approved status.
- Rejected Claims: Displays claims with Rejected status.

## 3. Forms vs Views

Forms display and help users work with one record at a time.

Views display multiple records and help users find and organise records.

## 4. Publishing

After modifying forms or views, save and publish the changes so they become available to users.
