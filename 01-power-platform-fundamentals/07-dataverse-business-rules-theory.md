# Dataverse Business Rules and Validation – Theory

## 1. What are Business Rules?

Business Rules allow makers to implement business logic and validation in Dataverse without writing code for common scenarios.

They control field behaviour, validate data and enforce business requirements.

**Example:** If Claim Status is Rejected, Rejection Reason should be displayed and required.

## 2. Components of Business Rules

- **Condition:** Checks whether a particular condition is satisfied.
- **Action:** Executes an operation based on the condition.
- **Scope:** Defines where the rule applies.

## 3. Common Business Rule Actions

| Action | Purpose |
|---|---|
| Set Business Required | Makes a field mandatory |
| Set Business Recommended | Marks a field as recommended |
| Set Value | Automatically populates a field |
| Set Visibility | Shows or hides a field |
| Set Field Requirement | Changes the requirement level |
| Lock / Unlock | Controls field editing |
| Show Error Message | Displays a validation error |

## 4. Conditions and Operators

Conditions determine when an action should execute.

Common operators include:
- Equals
- Does Not Equal
- Contains
- Does Not Contain
- Greater Than
- Less Than
- Greater Than or Equal To
- Less Than or Equal To
- Contains Data
- Does Not Contain Data

Multiple conditions can be combined using:

- AND: All conditions must be true.
- OR: At least one condition must be true.

## 5. Scope of Business Rules

- **Table:** Applies at the table level, subject to supported execution scenarios.
- **All Forms:** Applies to all main forms.
- **Specific Form:** Applies to a selected main form.

## 6. Business Rules vs Validation

Business Rules can enforce requirements such as mandatory fields, field visibility and value validation.

For example:
- Claim Amount must be greater than zero.
- Policy End Date must be later than Start Date.
- Rejection Reason must be provided for rejected claims.

## 7. Limitations

- Business Rules are suitable for simple business logic.
- Complex logic may require JavaScript, Power Automate or Dataverse plug-ins.
- Behaviour depends on the rule's scope and supported execution context.
- Business Rules do not replace all server-side validation.

## 8. Practical Applications

In an insurance management system, Business Rules can:
- Ensure valid claim amounts.
- Require rejection reasons.
- Validate policy dates.
- Prevent invalid premium and sum assured values.
- Make settlement information mandatory when required.
