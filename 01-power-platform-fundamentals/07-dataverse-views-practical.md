# Dataverse Views – Practical

## Objective

Create custom views for the Insurance Claim Management solution.

## 1. Insurance Claim Views

Table: Insurance Claim
<img width="1113" height="324" alt="image" src="https://github.com/user-attachments/assets/6110788b-297b-4f5f-8856-a7849c69da59" />

| View | Filter |
|---|---|
| Pending Claims | Claim Status = Submitted OR Under Review |
| Approved Claims | Claim Status = Approved |
| All Claims | No Claim Status filter |

<img width="1069" height="634" alt="image" src="https://github.com/user-attachments/assets/932b2df6-2b5f-4342-a343-acfdeb0dbba9" />
<img width="1069" height="634" alt="image" src="https://github.com/user-attachments/assets/e0ed4fbb-f8fe-47ac-9cb2-aff7d8657929" />
<img width="779" height="596" alt="image" src="https://github.com/user-attachments/assets/d8d30f31-4c32-4c3d-906b-d3a469e6d694" />

Columns used:
- Claim Number
- Claim Date
- Claim Amount
- Claim Status
- Insurance Policy

Sorting: Claim Date – Descending.

## 2. Insurance Policy Views

Table: Insurance Policy
<img width="1098" height="359" alt="image" src="https://github.com/user-attachments/assets/70fc057b-fed1-4a26-81a9-8bb0d69326ef" />

| View | Filter |
|---|---|
| Active Policies | Policy Status = Active |
| Expired Policies | Policy Status = Expired |
| Cancelled Policies | Policy Status = Cancelled |
| All Policies | No Policy Status filter |

<img width="1098" height="359" alt="image" src="https://github.com/user-attachments/assets/9de06f60-c4bc-4a73-88a3-edb1ae97c01e" />
<img width="1098" height="359" alt="image" src="https://github.com/user-attachments/assets/52bc9f3f-2168-4a00-933d-cbf3ec53f11b" />

Columns used:
- Policy Number
- Policy Name
- Policy Type
- Customer
- Premium Amount
- Sum Assured
- Start Date
- End Date
- Policy Status

## 3. Steps to Create a View

1. Open Power Apps Maker Portal.
2. Navigate to Solutions → Insurance Claim Management.
3. Open the required table → Views.
4. Select New View.
5. Enter the view name.
6. Add the required columns.
7. Configure filters using Edit Filters.
8. Configure sorting.
9. Save and Publish.
10. Open the model-driven app and test the view.

## 4. Verification

- Confirm custom views appear in the app's view selector.
- Verify that filters display the expected records.
- Verify that sorting works correctly.
- Confirm that All Claims and All Policies do not have custom status filters.
