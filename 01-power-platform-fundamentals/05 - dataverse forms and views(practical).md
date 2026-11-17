# 05 - Dataverse Forms and Views (Practical)

## 1. Objective

Customise Dataverse forms and understand how forms are used in a model-driven app to create, view, and edit records.

**Solution:** Insurance Claim Management

**Tables used:**
- Customer
- Insurance Policy
- Insurance Claim

---

## 2. Dataverse Forms

A Dataverse form is the user interface used to work with an individual record (row) in a Dataverse table.

### Types of Forms

| Form Type | Purpose |
|---|---|
| Main Form | Full interface for creating, viewing, and editing records. |
| Quick Create Form | Simplified form for quickly creating records. |
| Quick View Form | Displays selected information from a related record. |
| Card Form | Displays a compact representation of a record. |

---

## 3. Customising Main Forms

### Steps

1. Open the Power Apps Maker Portal.
2. Select the correct environment.
3. Navigate to **Solutions**.
4. Open **Insurance Claim Management**.
5. Open the required Dataverse table.
6. Select **Forms**.
7. Open the existing Main form.
8. Arrange fields and sections as required.
9. Select **Save**, followed by **Publish**.

### 3.1 Customer Main Form
<img width="2268" height="1382" alt="image" src="https://github.com/user-attachments/assets/e75c666a-5c4a-417b-9dac-0275cd50bb31" />

**Customer Information**
- Customer Name
- Customer Type

**Contact Information**
- Email
- Phone Number
- Address

**Personal Information**
- Date of Birth

### 3.2 Insurance Policy Main Form
<img width="2744" height="1530" alt="image" src="https://github.com/user-attachments/assets/dd9eb78d-c5d2-445b-846e-47dc21a36e9c" />

**Policy Information**
- Policy Name
- Policy Number
- Policy Type
- Policy Status

**Financial Information**
- Premium Amount
- Sum Assured

**Policy Duration**
- Start Date
- End Date

**Customer Information**
- Customer (Lookup)

### 3.3 Insurance Claim Main Form
<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/b87e7bfb-6457-4c21-8b09-3317fc582184" />

**Claim Information**
- Claim Name
- Claim Number
- Claim Date
- Claim Amount
- Claim Status

**Policy Information**
- Insurance Policy (Lookup)

**Review and Settlement**
- Rejection Reason
- Settlement Date
- Description

---

## 4. Model-Driven Apps
<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/6fac0f45-a4fc-4e15-8758-80c5047cfbc2" />

A model-driven app provides a user-facing interface for interacting with Dataverse tables, forms, views, and related data.

### Steps to Create a Model-Driven App

1. Navigate to **Solutions → Insurance Claim Management**.
2. Select **New → App → Model-driven app**.
3. Enter the app name: `Insurance Claim Management App`.
4. Open the app designer.
5. Select **Add page → Dataverse table**.
6. Add the following tables:
   - Customer
   - Insurance Policy
   - Insurance Claim
7. Save and Publish the app.
8. Select **Play** to launch the application.

*Note: Designer labels may vary slightly depending on the Power Apps version.*

---

## 5. Testing Forms in the Model-Driven App

After publishing the application, test the forms by creating records.
<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/152366f9-085a-4063-baef-fcbf40f9dfb2" />

### Step 1: Create a Customer
- Open the Customer table.
- Select **New**.
- Enter customer details.
- Save the record.

### Step 2: Create an Insurance Policy
- Open the Insurance Policy table.
- Select **New**.
- Enter policy details.
- Select an existing Customer using the Customer lookup.
- Save the record.

### Step 3: Create an Insurance Claim
- Open the Insurance Claim table.
- Select **New**.
- Enter claim details.
- Select an existing Insurance Policy using the lookup.
- Save the record.

### Record Creation Order

Customer → Insurance Policy → Insurance Claim

**Why this order?**

Lookup columns establish relationships between records. Therefore, the referenced record must exist before it can be selected in the lookup.

---

## 6. Autonumber Columns

Autonumber columns automatically generate unique identification values when records are created.

### Configuration

| Column | Autonumber Format | Example |
|---|---|---|
| Policy Number | `POL-{SEQNUM:5}` | POL-00001 |
| Claim Number | `CLM-{SEQNUM:5}` | CLM-00001 |

### Important Points

- Dataverse generates the number automatically when a record is created.
- The generated value may not appear immediately on a blank New form.
- Save the record and reopen it to check the generated number.
- Autonumber sequences can contain gaps. This is normal.
- Users should not manually enter values into autonumber fields.

### Making a Field Read-Only

The Claim Number field was configured as read-only using the form designer.

**Steps:**
1. Open the Insurance Claim Main form.
2. Select the Claim Number field.
3. Open its properties.
4. Enable the **Read-only** option.
5. Save and Publish the form.

**Important:** This is a form-level configuration. It does not make the Dataverse column globally read-only across all applications, integrations, or APIs.

---

## 7. Forms vs. Views

Forms and views serve different purposes in Dataverse.

| Forms | Views |
|---|---|
| Display an individual record. | Display multiple records in a list. |
| Used to create, view, and edit records. | Used to find, filter, and organise records. |
| Contain fields, tabs, and sections. | Contain columns, filters, and sorting. |
| Example: Customer Main Form. | Example: All Customers View. |

### Examples of Insurance Claim Views

- **All Claims:** Displays all insurance claims.
- **Pending Claims:** Displays claims awaiting review.
- **Approved Claims:** Displays approved claims.
- **Rejected Claims:** Displays rejected claims.

---

## 8. Key Takeaways

- Every Dataverse table can have multiple forms.
- Main forms provide the primary interface for working with individual records.
- Quick Create forms simplify record creation.
- Quick View forms display information from related records.
- Model-driven apps provide a user-friendly interface for Dataverse data.
- Lookup columns establish relationships between tables.
- Save stores changes, while Publish makes the changes available to users.
- Autonumber columns automatically generate identification numbers.
- Read-only settings configured in a form do not necessarily apply globally.
- Views help users filter, sort, and organise multiple records.

---

## 9. Practical Completed

**Solution:** Insurance Claim Management

**Completed Tasks:**
- Customised Customer Main form.
- Customised Insurance Policy Main form.
- Customised Insurance Claim Main form.
- Created a Model-Driven App.
- Added all three Dataverse tables to the app.
- Tested record creation and lookup relationships.
- Configured Policy Number and Claim Number as autonumber columns.
- Made Claim Number read-only on the form.
