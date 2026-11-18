# 06 - Dataverse Views (Theory and Practical)

## 1. Introduction to Views

A Dataverse View is used to display multiple records from a table in a structured list.

Views help users find, organise, filter and sort records without manually searching through the entire table.

### Example

An insurance company may have hundreds of insurance claims.

Instead of displaying every claim together, users can create separate views:

- All Claims
- Pending Claims
- Approved Claims
- Rejected Claims

Each view displays records based on specific conditions.

### Forms vs Views

| Forms | Views |
|---|---|
| Display one record at a time | Display multiple records |
| Used to create, view and edit records | Used to find and organise records |
| Contains fields and sections | Contains columns, filters and sorting |
| Example: Claim Form | Example: Pending Claims View |

---

## 2. Types of Dataverse Views

### 2.1 Public Views

- Available to users of the application, subject to their security permissions.
- Created by customisers or administrators.
- Can be included in model-driven apps.
- Useful for sharing commonly required record lists.

Example:
- All Customers
- Active Policies
- Pending Claims

### 2.2 System Views

- Built-in views provided by Dataverse.
- Also include custom system views created by administrators.
- Used by model-driven apps and Dataverse features.
- Examples include Active Records, Inactive Records, Associated View and Lookup View.

### 2.3 Personal Views

- Created by individual users for their own requirements.
- Can be shared with other users when permissions allow.
- Useful when users need customised record lists.

Example:

An employee creates a personal view to display claims assigned to them.

---

## 3. Components of a View

A Dataverse View mainly consists of the following components.

### 3.1 Columns

Columns determine which fields are displayed in the view.

Example: An Insurance Claim view may contain:

- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy

### 3.2 Filters

Filters determine which records are displayed.

Example:

To display only approved claims:

Claim Status = Approved

Only records satisfying the condition are displayed.

### 3.3 Sorting

Sorting determines the order in which records appear.

Examples:

- Ascending: Oldest to newest for dates.
- Descending: Newest to oldest for dates.
- Alphabetical ascending: A to Z.

### 3.4 Column Order

Determines the arrangement of columns in the view.

Example:

Claim Number → Claim Date → Claim Amount → Claim Status.

---

## 4. Filter Conditions

Filters allow users to display records based on specific conditions.

A filter condition generally consists of:

- Column: The field to evaluate.
- Operator: The comparison to perform.
- Value: The value to compare against.

Example:

| Column | Operator | Value |
|---|---|---|
| Claim Status | Equals | Approved |

This displays only claims whose status is Approved.

### Common Operators

| Operator | Meaning |
|---|---|
| Equals | Matches an exact value |
| Does not equal | Excludes a particular value |
| Contains | Contains specified text |
| Does not contain | Does not contain specified text |
| Begins with | Starts with specified text |
| Is greater than | Greater than a specified value |
| Is less than | Less than a specified value |
| On or before | Date is on or before a specified date |
| On or after | Date is on or after a specified date |

Available operators depend on the column's data type.

---

## 5. AND and OR Conditions

Dataverse supports logical operators to combine multiple filter conditions.

### 5.1 AND Operator

All conditions must be true for a record to appear.

Example:

Claim Status = Approved

AND

Claim Amount > 50000

Only approved claims with an amount greater than ₹50,000 are displayed.

### 5.2 OR Operator

At least one condition must be true.

Example:

Claim Status = Submitted

OR

Claim Status = Under Review

This displays both submitted and under-review claims.

### Difference Between AND and OR

| AND | OR |
|---|---|
| All conditions must be true | At least one condition must be true |
| Narrows the results | Includes records matching either condition |
| Used when multiple requirements must be satisfied | Used when alternative conditions are acceptable |

---

# PRACTICAL IMPLEMENTATION

## 6. Project: Insurance Claim Management

We use the following Dataverse tables:

1. Customer
2. Insurance Policy
3. Insurance Claim

The objective is to create useful views for managing insurance policies and claims.

---

## 7. Insurance Claim Views

### 7.1 Pending Claims

Purpose: Displays claims that are submitted or currently under review.

Columns:

- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy

Filter configuration:

| Column | Operator | Value |
|---|---|---|
| Claim Status | Equals | Submitted |
| Claim Status | Equals | Under Review |

Logical operator: OR

Filter logic:

Claim Status = Submitted

OR

Claim Status = Under Review

Sorting:
- Claim Date: Descending

### 7.2 Approved Claims

Purpose: Displays claims that have been approved.

Columns:

- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy

Filter:

Claim Status = Approved

Sorting:
- Claim Date: Descending

### 7.3 All Claims

Purpose: Displays all claims accessible to the user.

Columns:

- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy

Filter:
- No additional Claim Status filter.

Sorting:
- Claim Date: Descending

Note: Other default conditions, security permissions and record status can still affect the records displayed.

---

## 8. Insurance Policy Views

### 8.1 All Policies

Purpose: Displays all policies accessible to the user.

Columns:

- Policy Number
- Policy Name
- Policy Type
- Customer
- Premium Amount
- Sum Assured
- Start Date
- End Date
- Policy Status

Filter:
- No additional Policy Status filter.

### 8.2 Active Policies

Purpose: Displays policies whose business status is Active.

Filter:

Policy Status = Active

Sorting:
- End Date: Ascending

### 8.3 Expired Policies

Purpose: Displays policies whose business status is Expired.

Filter:

Policy Status = Expired

### 8.4 Cancelled Policies

Purpose: Displays policies whose business status is Cancelled.

Filter:

Policy Status = Cancelled

---

## 9. Difference Between Business Status and Dataverse Record Status

This is an important concept.

Dataverse maintains a built-in record status:

- State (Status): Active or Inactive.
- Status Reason: Explains the reason for the current state.

Our project also has custom Choice columns:

- Policy Status: Active, Expired, Cancelled.
- Claim Status: Submitted, Under Review, Approved, Rejected, Settled.

These are separate concepts.

### Example

| Claim Status (Custom Choice) | Dataverse Record Status |
|---|---|
| Submitted | Active |
| Under Review | Active |
| Approved | Active |
| Rejected | Active until deactivated |
| Settled | Inactive after closure |

The mapping above is an example business-process design. Dataverse does not automatically deactivate a record when its Claim Status changes to Rejected or Settled.

Similarly, Policy Status = Expired does not automatically make the Dataverse record Inactive.

---

## 10. Steps to Create a Custom View

1. Open Power Apps Maker Portal.
2. Select the required environment.
3. Navigate to Solutions.
4. Open the Insurance Claim Management solution.
5. Open the required Dataverse table.
6. Select Views.
7. Select New View.
8. Enter the view name and description.
9. Add the required columns.
10. Configure filter conditions using Edit Filters.
11. Configure sorting.
12. Save and publish the view.
13. Open the model-driven app and test the view.

---

## 11. Testing Views in a Model-Driven App

1. Open the Insurance Claim Management App.
2. Navigate to Insurance Claims.
3. Open the view selector.
4. Select Pending Claims.
5. Verify that only Submitted and Under Review claims appear.
6. Select Approved Claims.
7. Verify that only Approved claims appear.
8. Select All Claims.
9. Verify that all accessible matching claims appear.

Repeat the process for the Insurance Policy table.

---

## 12. Important Points to Remember

- A view displays multiple records.
- A form displays an individual record.
- Columns determine the fields displayed.
- Filters determine which records are included.
- Sorting determines the order of records.
- AND requires all conditions to be true.
- OR requires at least one condition to be true.
- Public views can be shared through an application, subject to security permissions.
- Personal views are created by individual users.
- System views include built-in and custom system-managed views.
- Publishing makes customisations available to users.
- A view does not change the underlying Dataverse records.
- Dataverse Active/Inactive status is different from custom Choice columns such as Claim Status and Policy Status.

## 13. Real-World Applications

| Department | Useful Views |
|---|---|
| Customer Service | All Customers, Active Customers |
| Insurance Operations | Pending Claims, Approved Claims |
| Claims Management | Rejected Claims, Settled Claims |
| Policy Administration | Active Policies, Expired Policies |
| Management | High-Value Claims, Policies Expiring Soon |

Views help organisations organise large amounts of business data and provide users with relevant information based on their responsibilities.
