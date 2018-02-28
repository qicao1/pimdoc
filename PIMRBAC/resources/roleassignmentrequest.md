# `roleAssignmentRequest`
Represents the request for role assignment operations. The request can be about:
* creating a new `roleAssignment`: users activate a role or administrators assigns a role to a user or group;
* removing a `roleAssignment`;
* updating a `roleAssignment`: such as administrators want to change start and end time for existing assignments; extending an expiring `roleAssignment`;

### Methods

| Method		  |Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleAssignmentRequests](../api/roleassignmentrequest_list.md) | [roleAssignmentRequest collection](roleassignmentrequest.md) |Get roleAssignmentRequest collection.|
|[Create a roleAssignmentRequest](../api/roleassignmentrequest_post.md) | [roleAssignmentRequest](roleassignmentrequest.md)	|Create roleAssignmentRequest object. |
|[Cancel a roleAssignmentRequest](../api/roleassignmentrequest_cancel.md)|  [roleAssignmentRequest](roleassignmentrequest.md)|Cancel a pending role assignment request.|
|[UpdateAdminDecision](../api/roleassignmentrequest_updateadmindecision.md)| [roleAssignmentRequest](roleassignmentrequest.md)|Approve or deny a role assignment request for extending a role assignment.|

### Properties
| Property	   | Type	| Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| The id of the role assignment request.|
|resourceId|String| The id of the resource which the role assignment request is associated with.|
|roleDefinitionId|String| The id of the role definition which the role assignment request is associated with.|
|subjectId|String| The id of the subject which the role assignment request is associated with.|
|type|String| The type of the role assignment request. The value can be <ul><li>`AdminAdd`: An adminstrator assign a user or group to a role;</li><li>`UserAdd`: An user activate his eligible role assignment;</li><li> `AdminUpdate`: An adminstrator changes existing role assignments</li><li>`AdminRemove`: An adminstrator removes a user or group from a role;<li>`UserRemove`: a user deactivate an active role assignment;<li>`UserExtend`: a user requests to extend expiring role assignments;</li><li>`AdminExtend`: an administrator extends an expiring role assignment for a user or group.</li></ul>|
|assignmentType|String|The role assignment type. The value can be ``Eligible`` - _"just in time"_ assignment, and ``Member`` - _"direct"_ assignment.|
|requestedDateTime|DateTimeOffset|The request create time. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|roleAssignmentStartDateTime|DateTimeOffset| The start time for the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|roleAssignmentEndDateTime|DateTimeOffset|The end time for the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|schedule|[schedule](schedule.md)| The schedule object of the role assignment request.|
|reason|String|The user provided reason for the role assignment request.|
|status|String|The status of the role assignment request. The value can be ``Accepted``, ``PendingEvaluation``, ``Granted``, ``Denied``, ``PendingProvisioning``, ``Provisioned``, `` PendingRevocation``, ``Revoked``, ``Canceled``, ``Failed``, ``PendingApprovalProvisioning``, ``PendingApproval`` and `PendingAdminDecision`.|
|statusDetail|[KeyValue](keyvalue.md) collection|The details of the request status.|
|targetLinkedRoleAssignmentId|String| The target linked role assignment id. For example, when a user tries to activate an eligible role assignment, TargetLinkedRoleAssignmentId will be the eligible role assignment id in the request. |
|evaluateOnly|Boolean|Indicates if the role assignment is for evaluation purpose only.|


### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|roleDefinition|[roleDefinition](roledefinition.md)|The role definition that the request aims to. |
|subject|[subject](subject.md)| The  user/group principal.|

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "resourceId": "String",
  "roleDefinitionId": "String",
  "subjectId": "String",
  "type": "String",
  "assignmentType": "String",
  "evaluateOnly": true,
  "reason": "String",
  "requestedDateTime": "String (timestamp)",
  "roleAssignmentStartDateTime": "String (timestamp)",
  "roleAssignmentEndDateTime": "String (timestamp)",
  "schedule": {"@odata.type": "microsoft.graph.schedule"},
  "status": "String",
  "statusDetail": [{"@odata.type": "microsoft.graph.KeyValue"}],
  "targetLinkedRoleAssignmentId": "String"
}

```