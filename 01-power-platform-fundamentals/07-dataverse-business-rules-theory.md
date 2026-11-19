# 07 - Dataverse Business Rules (Theory)

## 1. Introduction

Dataverse Business Rules allow developers and makers to apply business logic and validation to table data without writing JavaScript or C# code.

They help control:
- Field visibility
- Field requirements
- Field values
- Field editability
- Data validation
- Error messages

**Example:** When a claim status becomes Settled, the Settlement Date field should become visible and mandatory.

## 2. Why Business Rules Are Used

Business Rules help:
- Maintain data accuracy and consistency.
- Prevent invalid data entry.
- Reduce manual validation.
- Improve user experience.
- Implement simple business logic without code.
- Enforce standard business requirements.

## 3. Components of a Business Rule

A Business Rule consists of three main components.

### A. Condition

A condition defines when a rule should execute.

Examples:
- Claim Status equals Settled.
- Claim Amount is less than or equal to zero.
- Policy Status equals Cancelled.
- Email contains data.

Common operators:
- Equals
- Does Not Equal
- Contains Data
- Does Not Contain Data
- Greater Than
- Greater Than or Equal To
- Less Than
- Less Than or Equal To

### B. Actions

Actions define what happens when a condition evaluates to true or false.

| Action | Purpose |
|---|---|
| Set Business Required | Makes a field mandatory |
| Set Business Recommended | Recommends entering a value |
| Set Visibility | Shows or hides a field |
| Set Field Value | Automatically sets a field value |
| Set Default Value | Sets a default field value |
| Lock | Makes a field read-only |
| Unlock | Allows a field to be edited |
| Show Error Message | Displays a validation error |

### C. Scope

Scope determines where the Business Rule is applied.

| Scope | Description |
|---|---|
| Entity | Applies at the table level where supported |
| All Forms | Applies to all supported forms of the table |
| Specific Form | Applies to a selected form |

**Important:** Form-level actions such as visibility and locking need a form context. Entity-level rules and form-level rules have different execution capabilities.

## 4. Types of Business Rule Conditions

Conditions can be used to validate:

**Field values**
- Claim Amount > 0
- Premium Amount <= Sum Assured

**Field availability**
- Email contains data.
- Settlement Date does not contain data.

**Choice values**
- Claim Status = Rejected
- Policy Status = Cancelled

## 5. Business Rules vs Column Requirements

Dataverse provides three column requirement levels:

| Requirement | Meaning |
|---|---|
| Optional | The field can be left blank |
| Business Recommended | A value is recommended |
| Business Required | A value is required |

Column-level requirements are appropriate when a value must always be supplied.

Business Rules are useful when requirements depend on conditions.

Example:

- Claim Date: Always required.
- Settlement Date: Required only when Claim Status = Settled.
- Rejection Reason: Required only when Claim Status = Rejected.

## 6. Business Rules vs Other Validation Approaches

| Approach | Best suited for |
|---|---|
| Column requirements | Mandatory fields |
| Business Rules | Simple conditional form logic |
| Power Automate | Workflow and automation |
| Dataverse Plug-ins | Complex server-side validation |
| JavaScript | Advanced client-side form behaviour |

## 7. Limitations of Business Rules

- They are not suitable for complex business logic.
- They cannot generally compare a field with a value retrieved from a related table through a lookup.
- Form-level behaviour does not guarantee validation through every external API or integration.
- Date-based automation and multi-record calculations may require other tools.
- They should not replace server-side validation for critical business requirements.

## 8. Best Practices

1. Use column-level requirements for fields that are always mandatory.
2. Use Business Rules for conditional requirements.
3. Display error messages that clearly explain the problem.
4. Avoid making unrelated fields mandatory.
5. Test both If Yes and If No branches.
6. Validate rules through the actual model-driven app.
7. Use server-side validation for important financial and business constraints.

## 9. Key Takeaways

- Business Rules implement simple business logic without code.
- Conditions determine when actions execute.
- Actions control fields and validation.
- Scope determines where rules apply.
- Column requirements and Business Rules serve different purposes.
- Complex validation may require Power Automate or Dataverse plug-ins.
