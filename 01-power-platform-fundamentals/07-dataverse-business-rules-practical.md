# Dataverse Business Rules and Validation – Practical

## Objective

Implement business rules for the Insurance Claim Management solution.

## 1. Insurance Claim Table

Created the following Business Rules:

| Business Rule | Condition / Requirement |
|---|---|
| Claim Amount must be greater than zero | Claim Amount must be greater than 0 |
| Show Rejection Reason When Claim Rejected | Claim Status = Rejected |
| Set Settlement Date as mandatory | Claim Status = Settled |

<img width="1038" height="598" alt="image" src="https://github.com/user-attachments/assets/a836cfad-1c69-4456-a4d7-25ddee38c0b3" />

### Expected Behaviour

- Invalid claim amounts should be rejected.
- Rejection Reason is displayed when a claim is rejected.
- Settlement Date becomes mandatory when a claim is settled.

## 2. Insurance Policy Table

Created the following Business Rules:

| Business Rule | Purpose |
|---|---|
| Cancellation Reason | Controls cancellation-related information |
| Validate Policy Dates | Ensures valid policy date entries |
| Validate Premium Amount | Validates premium amount |
| Validate Sum Assured | Validates sum assured |

## 3. Steps to Create a Business Rule

1. Open Power Apps Maker Portal.
2. Navigate to Solutions → Insurance Claim Management.
3. Open the required table → Business Rules.
4. Select New Business Rule.
5. Add the required condition.
6. Add the corresponding action.
7. Configure the rule scope.
8. Validate the rule.
9. Save and Activate.

## 4. Verification

- Confirm that the Business Rule is activated.
- Test the condition using the model-driven app.
- Verify that the expected action occurs.
- Try invalid values to test validation.
- Verify that valid records can still be saved.
