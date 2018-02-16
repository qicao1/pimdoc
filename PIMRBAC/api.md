# Onboarding PIM for Azure RBAC APIs to Graph

## Contacts

Role|Name
----|----------------------
PM  |Steve Lieberman  (stlieber)
Eng |Qi Cao (qicao)
Eng |Nan Wu (nawu)

## Scenarios
With Privileged Identity Management (PIM) for Azure RBAC roles, you can manage, control, and monitor access to Azure resources within your organization.
* A user can see subscriptions, resource groups and other Azure resources that he has access to; roles, role assignments, assignment requests and role settings for a given resource; 
* A user can activate his eligible roles to get access to a resource, and deactivate when the access is not needed;
* A user can request to extend his expiring assignments, or renew his expired ones; cancel his pending role assignment requests;
* A user can see a history of his activities on role assignments and activations.
* An administrator can assign a role to a user or group; remove a role from a user or group; update role assignments, extend expiring ones, and renew expired ones; manage role settings for  roles;
* An administrator can approve or deny users' requests to renew/extend role assignments; 
* An administrator can see the activity history of role assignments and activations of all users for a given resource;
* An administrator can also get alerts about changes in role assignments for a given resource, and also manage these alerts.

## Schema changes

### New entity types
 *  [`tenant`](./resources/tenant.md)
 *  [`scenario`](./resources/scenario.md)
 *  [`resource`](./resources/resource.md)
 *  [`subject`](./resources/subject.md)
 *  [`roleDefinition`](./resources/roleDefinition.md)
 *  [`roleSetting`](./resources/roleSetting.md)
 *  [`roleAssignment`](./resources/roleAssignment.md)
 *  [`roleAssignmentRequest`](./resources/roleAssignmentRequest.md)
 *  [`alert`](./resources/alert.md)
 *  [`alertSetting`](./resources/alertSetting.md)
 *  [`alertDefinition`](./resources/alertDefinition.md)
 *  [`activity`](./resources/activity.md)
 *  [`target`](./resources/target.md)

### New complex types
* [`schedule`](./resources/schedule.md)
* [`recurrence`](./resources/recurrence.md)
* [`recurrenceItem`](./resources/recurrenceItem.md)
* [`recurrenceExclusion`](./resources/recurrenceExclusion.md)
* [`recurrenceType`](./resources/recurrenceType.md)
* [`KeyValue`](./resources/KeyValue.md)
* [`KeyValueList`](./resources/KeyValueList.md)
* [`ruleSetting`](./resources/ruleSetting.md)
* [`permission`](./resources/permission.md)

### New functions and actions

* [`permissions`](./api/resource_permissions.md) function on [`resource`](./resources/resource.md) entity;
*   [`cancel`](./api/roleassignmentrequest_cancel.md), [`adminUpdate`](./api/roleassignmentrequest_adminupdate.md) and [`updateAdminDecision`](./api/roleassignmentrequest_updateadmindecision) action on [`roleAssignmentRequest`](./resources/roleAssignmentRequest.md) entity;
*   [`refresh`](./api/alert_refresh.md), [`deactivate`](./api/alert_deactivate.md), [`disable`](./api/alert_disable.md), [`enable`](./api/alert_enable.md), and [`fix`](./api/alert_fix.md) actions on [`alert`](./resources/alert.md) entity;
*    [`getMyAssignments`](./api/roleassignment_getMyAssignments.md) and [`export`](./api/roleassignment_export.md) on [`roleAssignment`](./resources/roleAssignment.md) entity;
* [`export`](./api/activity_export.md) and [`getExpiredAssignmentAudits`](./api/activity_getexpiredassignmentaudits.md) on [`activity`](./resources/activity.md) entity;      

### New entity container

 Added a new entity container `Container`, which contains new entity sets of 
`registration`, `scenarios`, `resources`, `subjects`, `roleDefinitions`, `roleSettings`, `roleAssignments`, `roleAssignmentRequests`, `alerts`, and `activities`.

```xml
      <EntityContainer Name="Container">
        <EntitySet Name="registrations" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.tenant" />
        <EntitySet Name="scenarios" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.scenario" />
        <EntitySet Name="resources" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource" />
        <EntitySet Name="subjects" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.subject" />
        <EntitySet Name="alerts" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.alert" />
        <EntitySet Name="roleDefinitions" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition" />
        <EntitySet Name="roleAssignmentRequests" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignmentRequest" />
        <EntitySet Name="roleAssignments" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignment">
          <NavigationPropertyBinding Path="linkedAssignment" Target="roleAssignments" />
        </EntitySet>
        <EntitySet Name="roleSettings" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleSetting" />
        <EntitySet Name="activities" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.activity" />
      </EntityContainer>
```

