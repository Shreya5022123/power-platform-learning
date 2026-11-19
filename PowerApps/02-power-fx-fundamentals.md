# Power Fx Fundamentals

## 1. Introduction to Power Fx

Power Fx is the low-code formula language used in Microsoft Power Apps to implement application logic and behaviour.

It is similar to Excel formulas but is designed for building interactive business applications.

### Uses of Power Fx

- Display dynamic values and messages.
- Perform calculations.
- Implement conditional logic.
- Store and manage variables.
- Navigate between screens.
- Validate user input.
- Retrieve and update Dataverse records.
- Control the visibility and behaviour of controls.

### Example

```powerfx
If(
    Value(txtClaimAmount.Text) > 0,
    "Valid Claim Amount",
    "Enter a valid amount"
)
```

This checks whether the entered claim amount is greater than zero.

---

## 2. Where Power Fx Is Used

Power Fx formulas are assigned to properties of controls and screens.

There are two important categories of formulas.

### A. Property Formulas

Property formulas define how a control looks, what it displays, or what data it contains.

| Property | Example | Purpose |
|---|---|---|
| Text | `"Welcome"` | Displays text |
| Visible | `true` | Makes a control visible |
| DisplayMode | `DisplayMode.Disabled` | Disables a control |
| Items | `Insurance Claim` | Provides data to a control |
| Fill | `RGBA(0, 100, 200, 1)` | Sets background colour |

### B. Behavior Formulas

Behavior formulas perform actions in response to user interactions or application events.

They are commonly written in properties such as `OnSelect`, `OnVisible`, and `OnChange`.

Examples:

```powerfx
// Navigate to another screen
Navigate(ClaimSubmissionScreen)

// Store a value
Set(varUserName, "Shreya")

// Display a notification
Notify("Claim submitted successfully", NotificationType.Success)
```

**Difference:**

- Property formulas define a control's value or appearance.
- Behavior formulas execute actions.

---

## 3. Data Types in Power Fx

Power Fx supports different data types to represent application information.

| Data Type | Example | Description |
|---|---|---|
| Text | `"Rahul"` | Stores text values |
| Number | `5000` | Stores numeric values |
| Boolean | `true` | Represents true or false |
| Date | `Today()` | Represents a date |
| Record | `First(Customer)` | Represents one record |
| Table | `Customer` | Represents multiple records |
| Blank | `Blank()` | Represents an empty value |

### Examples

```powerfx
// Text
"Insurance Claim"

// Number
5000

// Boolean
true

// Current date
Today()

// First customer record
First(Customer)

// Empty value
Blank()
```

---

## 4. Operators in Power Fx

Operators are used to perform calculations, comparisons, and logical operations.

### Comparison Operators

| Operator | Meaning | Example |
|---|---|---|
| `=` | Equal to | `ClaimAmount = 5000` |
| `<>` | Not equal to | `ClaimStatus <> "Approved"` |
| `>` | Greater than | `ClaimAmount > 0` |
| `<` | Less than | `ClaimAmount < 10000` |
| `>=` | Greater than or equal to | `Age >= 18` |
| `<=` | Less than or equal to | `Age <= 60` |

### Logical Operators

| Operator | Meaning | Example |
|---|---|---|
| `&&` | AND | `Amount > 0 && Amount < 10000` |
| `||` | OR | `Status = "Approved" || Status = "Rejected"` |
| `!` | NOT | `!IsBlank(ClaimAmount)` |

### Text Concatenation Operator

The `&` operator joins text values.

```powerfx
"Welcome " & "Rahul"
```

Output:

```text
Welcome Rahul
```

---

## 5. Conditional Functions

Conditional functions allow applications to execute different logic depending on specified conditions.

### A. If()

The `If()` function checks a condition and returns a result based on whether it is true or false.

**Syntax:**

```powerfx
If(Condition, ResultIfTrue, ResultIfFalse)
```

**Example:**

```powerfx
If(
    Value(txtClaimAmount.Text) > 0,
    "Valid Claim Amount",
    "Enter a valid amount"
)
```

Explanation:
- If the claim amount is greater than zero, display `Valid Claim Amount`.
- Otherwise, display `Enter a valid amount`.

### B. Switch()

The `Switch()` function compares an expression against multiple possible values and returns the corresponding result.

**Syntax:**

```powerfx
Switch(
    Expression,
    Match1, Result1,
    Match2, Result2,
    DefaultResult
)
```

**Example:**

```powerfx
Switch(
    ddClaimStatus.Selected.Value,
    "Approved", "Claim Approved",
    "Rejected", "Claim Rejected",
    "Submitted", "Claim Submitted",
    "Status Not Available"
)
```

### If() vs Switch()

| If() | Switch() |
|---|---|
| Evaluates conditions. | Compares one expression against multiple values. |
| Suitable for complex logical conditions. | Suitable for multiple possible outcomes. |
| Can combine conditions using AND/OR. | Makes multiple value comparisons easier to read. |

---

## 6. Variables in Power Apps

Variables store values that can be reused within an application.

Power Apps provides three commonly used ways to manage variable data:

1. Global variables
2. Context variables
3. Collections

### A. Global Variables – Set()

Global variables can be accessed from anywhere in the application.

**Syntax:**

```powerfx
Set(VariableName, Value)
```

**Example:**

```powerfx
Set(varUserName, "Shreya")
```

To display the variable in a Label's `Text` property:

```powerfx
varUserName
```

To update its value:

```powerfx
Set(varUserName, "Rahul")
```

**Use cases:**
- Storing logged-in user information.
- Maintaining selected record information.
- Sharing application-level values across screens.

### B. Context Variables – UpdateContext()

Context variables are available only within the screen where they are created.

**Syntax:**

```powerfx
UpdateContext({VariableName: Value})
```

**Example:**

```powerfx
UpdateContext({showMessage: true})
```

To control a Label's `Visible` property:

```powerfx
showMessage
```

To hide the label:

```powerfx
UpdateContext({showMessage: false})
```

**Use cases:**
- Showing or hiding controls.
- Managing screen-specific messages.
- Controlling temporary UI states.

### Global Variables vs Context Variables

| Global Variable | Context Variable |
|---|---|
| Created using `Set()`. | Created using `UpdateContext()`. |
| Available throughout the app. | Available only on the current screen. |
| Useful for shared application data. | Useful for screen-specific state. |

### C. Collections

Collections are temporary in-memory tables that store multiple records or values.

They can be accessed across screens in the application.

Common functions:

| Function | Purpose |
|---|---|
| `Collect()` | Adds records to a collection. |
| `ClearCollect()` | Clears a collection and adds new records. |
| `Clear()` | Removes all records from a collection. |

Example:

```powerfx
ClearCollect(
    colClaims,
    {ClaimType: "Health", Amount: 5000},
    {ClaimType: "Life", Amount: 10000}
)
```

This creates a collection named `colClaims` containing two records.

To add another record:

```powerfx
Collect(
    colClaims,
    {ClaimType: "Vehicle", Amount: 8000}
)
```

**Important:** Collections are held in the app's memory. They are not automatically saved to Dataverse.

---

## 7. Navigation Functions

Navigation functions allow users to move between screens in a Canvas App.

### A. Navigate()

Moves the user to a specified screen.

**Syntax:**

```powerfx
Navigate(ScreenName)
```

**Example:**

```powerfx
Navigate(ClaimSubmissionScreen)
```

A screen transition can also be specified:

```powerfx
Navigate(
    ClaimSubmissionScreen,
    ScreenTransition.Fade
)
```

Common transitions include:
- `ScreenTransition.None`
- `ScreenTransition.Fade`
- `ScreenTransition.Cover`
- `ScreenTransition.UnCover`

### B. Back()

Returns to the previously visited screen.

```powerfx
Back()
```

### Example: Home Screen Navigation

| Button | OnSelect Formula |
|---|---|
| Submit New Claim | `Navigate(ClaimSubmissionScreen)` |
| View My Claims | `Navigate(MyClaimsScreen)` |
| Back | `Back()` |

---

## 8. Notification Functions

The `Notify()` function displays messages to users.

**Syntax:**

```powerfx
Notify(Message, NotificationType)
```

### Notification Types

| Type | Purpose |
|---|---|
| `NotificationType.Success` | Displays a success message. |
| `NotificationType.Error` | Displays an error message. |
| `NotificationType.Warning` | Displays a warning message. |
| `NotificationType.Information` | Displays an informational message. |

### Examples

Success notification:

```powerfx
Notify(
    "Claim submitted successfully",
    NotificationType.Success
)
```

Error notification:

```powerfx
Notify(
    "Please enter a valid claim amount",
    NotificationType.Error
)
```

---

## 9. Important Data Handling Functions

Power Fx provides functions to retrieve, filter, create, and update data.

| Function | Purpose |
|---|---|
| `IsBlank()` | Checks whether a value is empty. |
| `CountRows()` | Counts the number of records in a table. |
| `First()` | Returns the first record from a table. |
| `Filter()` | Returns records matching a condition. |
| `LookUp()` | Finds the first record matching a condition. |
| `Refresh()` | Refreshes a data source. |
| `Patch()` | Creates or updates records. |
| `SubmitForm()` | Submits a form control's data. |
| `ResetForm()` | Resets a form control. |

### Examples

Check whether a value is empty:

```powerfx
IsBlank(txtClaimAmount.Text)
```

Count records:

```powerfx
CountRows('Insurance Claim')
```

Retrieve the first record:

```powerfx
First('Insurance Claim')
```

Refresh a Dataverse table:

```powerfx
Refresh('Insurance Claim')
```

**Note:** `Filter()`, `LookUp()`, `Patch()`, and `SubmitForm()` will be covered in more detail during data operations and Dataverse integration.

---

## 10. Practical Implementation – Insurance Claim Management

### Objective

Implement basic navigation and user interaction in the Insurance Claim Management Canvas App.

### Step 1: Create Screens

Create the following screens:

- `HomeScreen`
- `ClaimSubmissionScreen`
- `MyClaimsScreen`

### Step 2: Configure Home Screen Navigation

Select the Submit New Claim button and set its `OnSelect` property:

```powerfx
Navigate(
    ClaimSubmissionScreen,
    ScreenTransition.Fade
)
```

Select the View My Claims button and set its `OnSelect` property:

```powerfx
Navigate(
    MyClaimsScreen,
    ScreenTransition.Fade
)
```

### Step 3: Add a Dynamic Welcome Message

Add a Label to the Home Screen.

Set its `Text` property:

```powerfx
"Welcome, " & User().FullName
```

This displays the name of the currently signed-in user.

### Step 4: Add Back Navigation

Add a Back button to the Claim Submission and My Claims screens.

Set its `OnSelect` property:

```powerfx
Back()
```

### Step 5: Test the Application

1. Preview the Canvas App.
2. Click Submit New Claim.
3. Verify that the Claim Submission screen opens.
4. Click Back.
5. Click View My Claims.
6. Verify that the My Claims screen opens.

---

## 11. Important Points to Remember

- Power Fx is the formula language used in Power Apps.
- Property formulas define values, appearance, and displayed data.
- Behavior formulas perform actions in response to events.
- `If()` and `Switch()` are used for conditional logic.
- `Set()` creates global variables.
- `UpdateContext()` creates screen-level context variables.
- `Collect()` and `ClearCollect()` manage collections.
- `Navigate()` and `Back()` handle screen navigation.
- `Notify()` displays messages to users.
- `Filter()` and `LookUp()` retrieve matching records.
- `Patch()` and `SubmitForm()` are used for data operations.
- Collections are temporary and are not automatically persisted to Dataverse.

## 12. Quick Revision

| Concept | Function / Property |
|---|---|
| Conditional logic | `If()`, `Switch()` |
| Global variable | `Set()` |
| Context variable | `UpdateContext()` |
| Create or update collection | `Collect()`, `ClearCollect()` |
| Navigate to screen | `Navigate()` |
| Return to previous screen | `Back()` |
| Display notification | `Notify()` |
| Check empty value | `IsBlank()` |
| Count records | `CountRows()` |
| Filter records | `Filter()` |
| Find a record | `LookUp()` |
| Refresh data | `Refresh()` |
| Create or update data | `Patch()` |
| Submit a form | `SubmitForm()` |
| Reset a form | `ResetForm()` |

---

**Next Topic:** Variables, Collections and Functions – practical application state management and working with collections in Canvas Apps.
