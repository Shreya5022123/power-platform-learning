# Power Apps – Canvas Apps

## 1. Introduction to Power Apps

Microsoft Power Apps is a low-code platform used to build custom business applications with minimal coding.

It allows users to create applications that connect to different data sources, automate business processes, and provide user-friendly interfaces.

### Types of Power Apps

| Canvas Apps | Model-Driven Apps |
|---|---|
| UI is designed manually using drag-and-drop controls. | UI is generated based on the data model. |
| Provides greater control over layout and design. | Follows a structured, data-centric layout. |
| Can connect to multiple data sources. | Requires Microsoft Dataverse. |
| Uses Power Fx for formulas and logic. | Uses Dataverse tables, forms, views, and relationships. |
| Suitable for customised user experiences. | Suitable for structured business processes. |

**Example: Insurance Claim Management**

- Canvas App: A customer-facing interface to submit an insurance claim.
- Model-Driven App: An internal application for employees to review and process claims.

---

## 2. Canvas App Fundamentals

A Canvas App provides a blank design surface where developers can create the application's interface.

The developer controls:
- Screen layout and navigation.
- Colours, fonts, and themes.
- Buttons, labels, forms, and galleries.
- User interactions.
- Data connections and formulas.

### Canvas App Layouts

- **Tablet:** Designed for larger screens such as desktops and tablets.
- **Phone:** Designed for mobile devices.

### Canvas App Structure

A Canvas App consists of screens, controls, properties, and formulas.

| Component | Description |
|---|---|
| App | The complete application. |
| Screen | An individual page within the application. |
| Control | An element placed on a screen. |
| Property | Defines a control's appearance or behaviour. |
| Formula | Defines logic or expressions using Power Fx. |

### Example Application Structure

Insurance Claim Management:

```text
Insurance Claim Management
│
├── HomeScreen
│   ├── Heading
│   ├── Welcome Label
│   ├── Submit Claim Button
│   └── View Claims Button
│
├── ClaimSubmissionScreen
│   ├── Claim Form
│   ├── Policy Dropdown
│   └── Submit Button
│
├── MyClaimsScreen
│   └── Claims Gallery
│
└── ClaimDetailsScreen
    └── Claim Information
```

---

## 3. Screens

A screen represents an individual page in a Canvas App.

An application can contain multiple screens, and users can navigate between them.

### Common Screens in a Business Application

| Screen | Purpose |
|---|---|
| Home Screen | Displays the application's landing page. |
| Submission Screen | Allows users to enter information. |
| Listing Screen | Displays multiple records. |
| Details Screen | Displays information about a selected record. |

### Important Screen Properties

| Property | Description |
|---|---|
| Fill | Sets the screen's background colour. |
| OnVisible | Executes a formula when the screen becomes visible. |
| OnHidden | Executes a formula when the screen is hidden. |

---

## 4. Controls

Controls are the visual elements used to build the application's interface and provide user interaction.

### Common Canvas App Controls

| Control | Purpose | Example |
|---|---|---|
| Label | Displays text. | Screen heading |
| Button | Performs an action when selected. | Submit Claim |
| Text Input | Accepts text or numeric input. | Claim Description |
| Dropdown | Allows selection from a list. | Claim Status |
| Combo Box | Allows searching and selecting one or more items. | Customer Selection |
| Gallery | Displays a collection of records. | My Claims |
| Form | Displays, creates, or edits a record. | Claim Form |
| Date Picker | Allows users to select a date. | Claim Date |
| Checkbox | Represents a true/false selection. | Terms Accepted |
| Image | Displays an image. | Company Logo |

### Example

For an Insurance Claim Submission screen:

- Text Input – Claim Description
- Text Input – Claim Amount
- Date Picker – Claim Date
- Dropdown – Insurance Policy
- Button – Submit Claim

---

## 5. Control Properties

Every control has properties that determine its appearance, data, and behaviour.

### Common Properties

| Property | Description |
|---|---|
| Text | Defines the text displayed by a control. |
| OnSelect | Defines the action performed when a control is selected. |
| Visible | Determines whether a control is visible. |
| DisplayMode | Controls whether a control is editable, disabled, or view-only. |
| Items | Defines the data displayed in controls such as galleries and dropdowns. |
| Default | Defines the initial value of a control. |
| X | Sets the horizontal position. |
| Y | Sets the vertical position. |
| Width | Defines the control's width. |
| Height | Defines the control's height. |
| Fill | Sets the background colour. |

### DisplayMode Values

| Value | Description |
|---|---|
| DisplayMode.Edit | Control is editable. |
| DisplayMode.View | Control is read-only. |
| DisplayMode.Disabled | Control is disabled. |

### Example Formulas

```powerfx
// Hide a control
false

// Show a control
true

// Disable a button
DisplayMode.Disabled

// Display a heading
"Insurance Claim Management"
```

---

## 6. Power Fx Introduction

Power Fx is the low-code formula language used in Microsoft Power Apps.

It is similar to Excel formulas and is used to define application behaviour, calculations, data operations, and user interactions.

### Examples

```powerfx
// Display text
"Welcome to Insurance Claim Management"

// Check a condition
If(10 > 5, "Valid", "Invalid")

// Store a value in a variable
Set(varName, "Shreya")

// Navigate to another screen
Navigate(ClaimSubmissionScreen)

// Display a notification
Notify("Claim submitted successfully", NotificationType.Success)
```

Power Fx formulas are written in the property formula bar of a control or screen.

---

## 7. Connecting Canvas Apps to Dataverse

Dataverse is a cloud-based data platform used to securely store and manage business data.

Canvas Apps can connect to Dataverse tables and use their records in the application.

### Architecture

```text
       Canvas App
            |
            v
    Dataverse Connector
            |
            v
        Dataverse
            |
    -------------------
    |        |        |
 Customer  Policy   Claim
  Table    Table    Table
```

### Connecting Dataverse to a Canvas App

1. Open the Canvas App in Power Apps Studio.
2. Open the **Data** pane.
3. Select **Add data**.
4. Choose **Microsoft Dataverse**.
5. Select the required tables.
6. Add the tables to the application.

### Insurance Claim Management Data Sources

| Dataverse Table | Purpose |
|---|---|
| Customer | Stores customer information. |
| Insurance Policy | Stores policy details. |
| Insurance Claim | Stores claim information. |

### Using Dataverse Tables in Power Fx

Once connected, tables can be referenced directly in formulas.

```powerfx
// Reference the Customer table
Customer

// Count customer records
CountRows(Customer)

// Retrieve the first customer record
First(Customer)

// Refresh the customer data source
Refresh(Customer)
```

**Important:** Adding a Dataverse table as a data source makes it available to the app. It does not automatically display its records on the screen. Controls such as galleries, forms, and dropdowns must be configured to use that data.

---

## 8. Canvas App Development Workflow

A typical Canvas App development process:

1. Create a Canvas App.
2. Select a layout (Tablet or Phone).
3. Create the required screens.
4. Add controls to each screen.
5. Configure control properties.
6. Connect the required data sources.
7. Write Power Fx formulas.
8. Implement navigation and user interactions.
9. Test the application.
10. Publish and share the application.

---

## 9. Key Takeaways

- Canvas Apps provide complete control over the application's user interface.
- Screens represent individual pages within an application.
- Controls are the building blocks of the interface.
- Properties define how controls look and behave.
- Power Fx is used to implement application logic.
- Dataverse provides structured data storage.
- Canvas Apps can connect to multiple data sources.
- Galleries and forms are commonly used to display and manage records.
