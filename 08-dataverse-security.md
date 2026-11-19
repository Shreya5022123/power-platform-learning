# Dataverse Security and Permissions

## 1. Introduction

Dataverse security controls **who can access data, what actions they can perform, and which records they can access**.

It uses a role-based security model to protect business data.

**Example – Insurance Claim Management**

- Claims Executive: Creates and updates claims.
- Claims Manager: Reviews, approves and assigns claims.
- Administrator: Has administrative access.

Not every user should have access to every operation or record.

## 2. Dataverse Security Architecture

```text
                 Dataverse Environment
                         |
                  Business Units
                         |
                    Users / Teams
                         |
                   Security Roles
                         |
                  Table Privileges
                         |
                  Access Levels
                         |
                  Record-Level Access
                         |
                Column-Level Security
```

Effective access is determined by the combination of privileges, access levels, ownership, team membership and record sharing.

## 3. Security Roles

A Security Role defines the operations a user or team can perform on Dataverse tables.

### Common Privileges

| Privilege | Description |
|---|---|
| Create | Create new records |
| Read | View records |
| Write | Modify existing records |
| Delete | Delete records |
| Append | Associate the current record with another record |
| Append To | Allow another record to be associated with this record |
| Assign | Change record ownership |
| Share | Share record access with others |

**Example:** A Claims Executive may have Create, Read and Write permissions on Insurance Claim but no Delete permission.

## 4. Access Levels

Privileges determine what a user can do. Access levels determine which records those privileges apply to.

| Access Level | Description |
|---|---|
| None | No access |
| User (Basic) | Records owned by the user, shared records and applicable team-owned records |
| Business Unit | Records within the user's Business Unit and User-level access |
| Parent: Child Business Units | Records in the user's Business Unit and its child units |
| Organization | Records across the entire organization |

### Example

```text
             Head Office
                  |
        ---------------------
        |         |         |
      Mumbai    Pune      Delhi
        |
   Claims Executive
```

A user with Business Unit-level Read access in Mumbai can access records within Mumbai's Business Unit, subject to other security settings.

## 5. Business Units

A Business Unit is a logical organisational boundary used to organise users and control access to records.

Key points:
- Every environment has a root Business Unit.
- Business Units can have parent-child relationships.
- Users belong to a Business Unit.
- Security roles can be assigned to users and teams.

**Example:** An insurance organisation can have separate Business Units for Mumbai, Pune and Delhi.

## 6. Teams

Teams allow organisations to manage access for groups of users.

### Types of Teams

| Owner Team | Access Team |
|---|---|
| Can own records | Cannot own records |
| Can have Security Roles | Cannot have Security Roles |
| Can provide access through team ownership and roles | Provides access to specific shared records |

**Example:** Multiple specialists can be given access to a particular insurance claim through an Access Team.

## 7. Column-Level Security

Column-Level Security restricts access to specific columns within a table.

It is useful when a user can access a record but should not see or modify certain sensitive fields.

### Column Security Permissions

| Permission | Purpose |
|---|---|
| Read | View the secured column |
| Create | Enter a value when creating a record |
| Update | Modify the column value |

Column security is configured through Column Security Profiles.

**Example:** A Claims Executive may view claim details but may not have permission to view a secured financial information column.

Note: Column security does not grant access to the record itself.

## 8. Record Ownership and Sharing

Dataverse records can be owned by individual users or Owner Teams, depending on the table's ownership type.

Record sharing allows access to a particular record to be granted to another user or team.

**Example:** A Claims Manager can share a specific claim with a specialist for review without changing its ownership.

## 9. Insurance Claim Management – Security Example

A possible permission design for our project:

| Operation | Claims Executive | Claims Manager | Administrator |
|---|---|---|---|
| View Claims | Yes | Yes | Yes |
| Create Claims | Yes | Yes | Yes |
| Update Claims | Yes | Yes | Yes |
| Delete Claims | No | No | Yes |
| Assign Claims | No | Yes | Yes |
| Share Claims | No | Yes | Yes |
| View Policies | Yes | Yes | Yes |

This is an example permission matrix, not an automatic Dataverse configuration.

## 10. Important Concepts

- Users can have multiple Security Roles.
- Security Roles can be assigned to users and teams.
- Privileges from multiple roles are cumulative.
- Access levels determine the scope of record access.
- Business Units organise users and records.
- Teams simplify access management for groups.
- Record sharing grants access to specific records.
- Column Security Profiles protect sensitive columns.
- Follow the Principle of Least Privilege: provide only the permissions required for a user's responsibilities.

## 11. When to Use What?

| Requirement | Security Feature |
|---|---|
| Control Create, Read, Update and Delete | Security Roles |
| Restrict access by organisational unit | Business Units |
| Manage permissions for a group | Teams |
| Restrict access to sensitive columns | Column Security |
| Give someone access to a particular record | Record Sharing |

## 12. Summary

Dataverse security is layered. Security Roles define privileges, access levels determine record scope, Business Units organise the organisation, Teams manage group access, and Column-Level Security protects sensitive fields.

Together, these features help organisations build secure and controlled business applications.
