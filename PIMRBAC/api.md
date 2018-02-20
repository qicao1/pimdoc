# Onboarding PIM for Azure RBAC APIs to Graph

## Contacts

Role|Name
----|----------------------
PM  |Steve Lieberman  (stlieber)
Eng |Qi Cao (qicao)
Eng |Nan Wu (nawu)

## Scenarios
With Privileged Identity Management (PIM) for Azure RBAC roles, you can manage, control, and monitor access to Azure resources within your organization.
* An administrator can assign a user or group to a role, by _"Just in time"_ assignment (activation required) or _"Direct"_ assignment (activation not required); remove a user or group from a role;
* An administrator can update existing role assignments;
* An administrator can extend expiring role assignments; 
* An administrator can manage role settings for roles.
* An administrator can approve or deny users' requests to extend role assignments, and cancel any pending requests of users; 
<!--
* An administrator can see the activity history of role assignments and activations of all users for a given resource;
* An administrator can also get alerts about changes in role assignments for a given resource, and also manage these alerts.
-->
* A user can see subscriptions, resource groups and other Azure resources that he has access to; roles, role assignments, assignment requests and role settings for a given resource; 
* A user can activate his eligible roles to get access to a resource, and deactivate when the access is not needed;
* A user can request to extend his expiring assignments; cancel his pending role assignment requests;
<!--
* A user can see a history of his activities on role assignments and activations.
-->

## Schema changes

### New entity types
 <!-- *  [`tenant`](./resources/tenant.md) -->
 *  [`scenario`](./resources/scenario.md)
 *  [`resource`](./resources/resource.md)
 *  [`subject`](./resources/subject.md)
 *  [`roleDefinition`](./resources/roledefinition.md)
 *  [`roleSetting`](./resources/roleSetting.md)
 *  [`roleAssignment`](./resources/roleassignment.md)
 *  [`roleAssignmentRequest`](./resources/roleassignmentrequest.md)
 <!--
 *  [`alert`](./resources/alert.md)
 *  [`alertSetting`](./resources/alertSetting.md)
 *  [`alertDefinition`](./resources/alertDefinition.md)
 *  [`activity`](./resources/activity.md)
 *  [`target`](./resources/target.md)
 -->

### New complex types
* [`schedule`](./resources/schedule.md)
* [`KeyValue`](./resources/KeyValue.md)
* [`ruleSetting`](./resources/ruleSetting.md)
* [`permission`](./resources/permission.md)
<!--
* [`KeyValueList`](./resources/KeyValueList.md)
* [`recurrence`](./resources/recurrence.md)
* [`recurrenceItem`](./resources/recurrenceItem.md)
* [`recurrenceExclusion`](./resources/recurrenceExclusion.md)
* [`recurrenceType`](./resources/recurrenceType.md)
-->


### New functions and actions

* [`permissions`](./api/resource_permissions.md) function on [`resource`](./resources/resource.md) entity;
* [`export`](./api/roleassignment_export.md) on [`roleAssignment`](./resources/roleAssignment.md) entity;
* [`cancel`](./api/roleassignmentrequest_cancel.md), and [`updateAdminDecision`](./api/roleassignmentrequest_updateadmindecision) action on [`roleAssignmentRequest`](./resources/roleassignmentrequest.md) entity;
<!--
* [`export`](./api/activity_export.md) and [`getExpiredAssignmentAudits`](./api/activity_getexpiredassignmentaudits.md) on [`activity`](./resources/activity.md) entity;  
*   [`refresh`](./api/alert_refresh.md), [`deactivate`](./api/alert_deactivate.md), [`disable`](./api/alert_disable.md), [`enable`](./api/alert_enable.md), and [`fix`](./api/alert_fix.md) actions on [`alert`](./resources/alert.md) entity;  
-->  

### New entity container

 Added a new entity container `Container`, which contains new entity sets of 
 `scenarios`, `resources`, `subjects`, `roleDefinitions`, `roleSettings`, `roleAssignments`, and `roleAssignmentRequests`.
<!-- `registration`, `alerts`, and `activities` -->

```xml
      <EntityContainer Name="Container">
        <EntitySet Name="scenarios" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.scenario" />
        <EntitySet Name="resources" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource" />
        <EntitySet Name="subjects" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.subject" />
        <EntitySet Name="roleDefinitions" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition" />
        <EntitySet Name="roleAssignmentRequests" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignmentRequest" />
        <EntitySet Name="roleAssignments" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignment">
          <NavigationPropertyBinding Path="linkedAssignment" Target="roleAssignments" />
        </EntitySet>
        <EntitySet Name="roleSettings" EntityType="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleSetting" />
      </EntityContainer>
```

