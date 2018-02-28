# Onboarding PIM for Azure RBAC APIs to Microsoft Graph

## Contacts

Role|Name
----|----------------------
PM  |Steve Lieberman  (stlieber)
Eng |Qi Cao (qicao)
Eng |Nan Wu (nawu)

## Scenarios
With Privileged Identity Management (PIM) for Azure RBAC roles, you can manage, control, and monitor access to Azure resources within your organization.
#### Persona: administrator
1. An administrator of a resource can see all roles, assignments, role settings, and assignment requests in this resource. 
2.  An administrator can assign a user or group to a role. There are 2 assignment types:
    *  _"Just in time"_ assignment: a user (or a member of a group) needs to activate the role to acquire just in time access to the resource. The assignment defines the time window of the eligiblity to activate the role.
    * _"Direct (time-based)"_ assignment: a user (or a member of a group) has direct access to the resource, and no activation is required. The assignment defines the time window of the access. 
3. An administrator can remove a user or group from a role.
4. An administrator can update existing role assignments, and extend expiring role assignments; 
5. An administrator can change settings for a role, such as maximum activation durations, MFA requirement on activation, etc.
6. An administrator can approve or deny users' requests to extend role assignments, and cancel any pending requests of users; 

#### Persona: user
1. A user can see all the resources that he can access to. 
    * For `pimforrbac` scenario, the resources could be subscriptions, resource groups and other Azure resources such as vitual machines, etc;
2. A user can see his role assignments and assignment requests for a resource he has access to; 
3. A user can activate his eligible roles to get access to a resource, and deactivate when the access is not needed;
4. A user can request to extend his expiring assignments; cancel his pending role assignment requests;

The scenarios above are well documented with examples in [`Scenarios`](scenarios.md).

## Schema changes

### Relationship to existing AAD PIM API in beta version
API of Privileged Identity Management for Azure Active Directory Roles (AAD PIM) is already onboarded to beta version, and developers can continue using this API to manage privileged roles for their azure active diretories.

However, Privileged Identity Management for Azure RBAC roles (RBAC PIM) is a new set of API built upon a new provider model. We are pushing an effort to introduce the concept of provider (represented by [`scenario`](./resources/scenario.md) in the new model) to indicate different realms of resources that PIM as a service can and will manage. Meanwhile, templatize common concepts in the new model like roles, assignments, requests, and etc, to be adaptive for different scenarios. In the end, the new model will be leveraged to serve new scopes for PIM, and developers only need to know a single set of API calling pattern to manage privileged access for different kinds of resources.

### New entity types
 *  [`scenario`](./resources/scenario.md)
 *  [`resource`](./resources/resource.md)
 *  [`subject`](./resources/subject.md)
 *  [`roleDefinition`](./resources/roledefinition.md)
 *  [`roleSetting`](./resources/rolesetting.md)
 *  [`roleAssignment`](./resources/roleassignment.md)
 *  [`roleAssignmentRequest`](./resources/roleassignmentrequest.md)

### New complex types
* [`schedule`](./resources/schedule.md)
* [`ruleSetting`](./resources/rulesetting.md)
* [`permission`](./resources/permission.md)


### New functions and actions

* [`permissions`](./api/resource_permissions.md) function on [`resource`](./resources/resource.md) entity;
* [`export`](./api/roleassignment_export.md) function on [`roleAssignment`](./resources/roleassignment.md) entity;
* [`cancel`](./api/roleassignmentrequest_cancel.md) and [`updateAdminDecision`](./api/roleassignmentrequest_updateadmindecision) actions on [`roleAssignmentRequest`](./resources/roleassignmentrequest.md) entity;

### New entity container

 Added a new entity container `PrivilegedIdentityManagementServiceContainer`, which contains new entity sets of 
 `scenarios`, `resources`, `subjects`, `roleDefinitions`, `roleSettings`, `roleAssignments`, and `roleAssignmentRequests`.

```xml
      <EntityContainer Name="PrivilegedIdentityManagementServiceContainer">
        <EntitySet Name="scenarios" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.scenario" />
        <EntitySet Name="resources" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource" />
        <EntitySet Name="subjects" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.subject" />
        <EntitySet Name="roleDefinitions" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition" />
        <EntitySet Name="roleAssignmentRequests" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignmentRequest" />
        <EntitySet Name="roleAssignments" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignment">
          <NavigationPropertyBinding Path="linkedEligibleAssignment" Target="roleAssignments" />
        </EntitySet>
        <EntitySet Name="roleSettings" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleSetting" />
      </EntityContainer>
```

