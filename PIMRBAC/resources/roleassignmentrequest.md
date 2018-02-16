# `roleAssignmentRequest`
Represents the request of role assignment operations. The request can be about:
* creating a new `roleAssignment`: users activate a role or administrators assigns a role to a user or group;
* removing a `roleAssignment`;
* updating a `roleAssignment`: such as administrators want to change start and end time for existing assignments; extending an expiring `roleAssignment`; renewing an expired `roleAssignment`;

### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleAssignmentRequests](../api/roleassignmentrequest_list.md) |  |  [roleAssignmentRequest collection](roleassignmentrequest.md) |Get roleAssignmentRequest collection.|
|[Create](../api/roleassignmentrequest_post.md) |  |  [roleAssignmentRequest](roleassignmentrequest.md)	|Create roleAssignmentRequest object. |
|[Cancel](../api/roleassignmentrequest_cancel.md)| `id` | [roleAssignmentRequest](roleassignmentrequest.md)|Cancel a pending role assignment request.|
|[UpdateAdminDecision](../api/roleassignmentrequest_updateadmindecision.md)| `id` | [roleAssignmentRequest](roleassignmentrequest.md)|Approve or deny a role assignment request for renewing or extending a role assignment.|

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓  | No|The id of the role assignment request. Read-only.|
|assignmentType|String|  | Yes|The role assignment type. The value can be ``Eligible`` and ``Member``.|
|requestType|String|  | Yes|The type of the role assignment request. The value can be ``AdminAdd``, ``UserAdd``, ``AdminUpdate``, ``AdminRemove``, and ``UserRemove``.|
|requestedDateTime|DateTimeOffset|  | Yes|The request create time. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|roleAssignmentStartDateTime|DateTimeOffset|  | Yes|The start time for the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|roleAssignmentEndDateTime|DateTimeOffset|  | Yes|The end time for the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|schedule|[schedule](schedule.md)|  | Yes|The schedule of the role assignment request.|
|reason|String|  | Yes|The user provided reason for the role assignment request.|
|status|String|  | Yes|The status of the role assignment request. The value can be ``Accepted``, ``PendingEvaluation``, ``Granted``, ``Denied``, ``PendingProvisioning``, ``Provisioned``, `` PendingRevocation``, ``Revoked``, ``Canceled``, ``Failed``, ``PendingApprovalProvisioning``, ``PendingApproval`` and `PendingAdminDecision`.|
|statusDetail|[KeyValue](keyvalue.md) collection|  | Yes|The details of the request status.|
|targetLinkedRoleAssignmentId|String|  | Yes|The target linked role assignment id. For example, when a user tries to activate an eligible role assignment, TargetLinkedRoleAssignmentId will be the eligible role assignment id in the request. |
|evaluateOnly|Boolean|  | Yes|Indicates if the role assignment is for evaluation purpose only.|


### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|roleDefinition|[roleDefinition](roledefinition.md)|The role definition that the request aims to. Read-only. Nullable.|
|subject|[subject](subject.md)| The  user/group principal. Read-only. Nullable.|

### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.roleAssignmentRequest"
}-->

```json
{
  "assignmentLevel": "String",
  "evaluateOnly": true,
  "id": "String (identifier)",
  "reason": "String",
  "requestType": "String",
  "requestedDateTime": "String (timestamp)",
  "roleAssignmentStartDateTime": "String (timestamp)",
  "schedule": {"@odata.type": "microsoft.graph.schedule"},
  "status": "String",
  "statusDetail": [{"@odata.type": "microsoft.graph.KeyValue"}],
  "targetLinkedRoleAssignmentId": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "roleAssignmentRequest resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->