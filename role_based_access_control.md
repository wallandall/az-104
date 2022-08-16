# Role Based Access Control

## Understanding Roles in Azure

Access management for cloud resources is a critical function for any organization that is using the cloud. Azure role-based access control (Azure RBAC) helps you manage ***who (Security Principal)*** has access to Azure resources, ***what (Role Definition)*** they can do with those resources, and ***what areas (Scope)*** they have access to.

1. A security principal is an object that represents a user, group, service principal, or managed identity that is requesting access to Azure resources. You can assign a role to any of these security principals.
2. A role definition is a collection of permissions. It's typically just called a role. A role definition lists the actions that can be performed, such as read, write, and delete. Roles can be high-level, like owner, or specific, like virtual machine reader.
3. Scope is the set of resources that the access applies to. When you assign a role, you can further limit the actions allowed by defining a scope. In Azure, you can specify a scope at four levels: management group, subscription, resource group, or resource. Scopes are structured in a parent-child relationship.

| Azure AD Roles                                                                                  | Azure RBAC                                                                                     |
| ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Manage access to Azure AD Resources                                                             | Manage access to Azure Resources                                                               |
| Scope is at tenant level                                                                        | Scope can be at muliple levels                                                                 |
| Supports custom roles                                                                           | Supports custom roles                                                                          |
| Main Roles:<br />1. Global Admin<br />2. User Administrator<br />3. Billing Administrator<br /> | Main Roles:<br />1. Owner<br />2. Contributor<br />3. Reader<br />4. User Access Administrator |

More information on roles can be found [here](https://docs.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles)


[Back](ReadMe.md)
