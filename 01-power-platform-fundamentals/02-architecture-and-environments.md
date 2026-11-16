# Power Platform Architecture and Environments

## 1. Power Platform Architecture

Power Platform consists of multiple interconnected layers.

- User Experience Layer: Power Apps, Power Pages, Copilot Studio.
- Business Logic and Automation Layer: Power Automate, business rules, Power Fx and custom logic.
- Data Layer: Dataverse, SQL Server, SharePoint and other data sources.
- Integration and Intelligence Layer: Connectors, APIs, AI Builder and Azure services.
- Security and Governance: Apply across the platform.

## 2. Component Communication

Example: Insurance Claim Management.

1. Power Apps: Employee enters claim information.
2. Dataverse: Stores claim information.
3. Power Automate: Triggers the approval workflow.
4. Connectors/APIs: Communicate with external systems.
5. Power BI: Displays claim reports and statistics.

## 3. Microsoft Tenant

A tenant is an organisation's dedicated Microsoft cloud identity boundary associated with Microsoft Entra ID.

It manages organisational identities, groups and access to Microsoft cloud resources.

## 4. Environment

An environment is a workspace where Power Platform resources are created, stored and managed.

It can contain:
- Power Apps.
- Power Automate flows.
- Dataverse database.
- Connections.
- Custom connectors.

## 5. Types of Environments

- Default: Automatically available for the tenant.
- Production: Used for live business applications.
- Sandbox: Used for development, testing and other non-production purposes.
- Developer: Individual environment for development and learning.
- Trial: Temporary environment for evaluating capabilities.

## 6. Development Lifecycle

Development -> Testing -> Production

- Development: Build and modify applications.
- Testing: Validate functionality and identify issues.
- Production: Deploy approved applications for actual users.

## 7. Tenant vs Environment

Tenant:
- Represents the organisation's Microsoft cloud identity boundary.
- Can contain multiple environments.

Environment:
- Represents a workspace within a tenant.
- Contains Power Platform resources.
- Has its own configuration and resource boundaries.

## 8. Dataverse

Dataverse is Microsoft's cloud-based data platform used to store and manage business information.

Example tables:
- Customer
- Policy
- Claim
- Employee

An environment can have its own Dataverse database.

Note: Not every Power Platform application requires Dataverse. Model-driven apps require Dataverse.

## 9. Power Platform Admin Center

Administration portal used to:
- Create and manage environments.
- Configure environment settings.
- Manage Dataverse-related settings.
- Monitor capacity and resources.
- Configure administration and governance settings.

Portal: https://admin.powerplatform.microsoft.com/
