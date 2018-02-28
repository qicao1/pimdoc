# `roleAssignment` entity
Represents the assignment of a user or group to a role.

### Methods

| Method		  | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleAssignments](../api/roleassignment_list.md) | [roleAssignment](roleassignment.md) |List roleAssignment collection.|
|[Get roleAssignment](../api/roleassignment_get.md) |  [roleAssignment](roleassignment.md) |Read properties and relationships of roleAssignment object.|
|[Export roleAssignment](../api/roleassignment_export.md) | octet-stream |Download a list of role assignments and save as a `.csv` file.|

### Properties
| Property	   | Type	| Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String|  The id of the role assignment. |
|resourceId|String|  The id of the resource which the role assignment is associated with. |
|roleDefinitionId|String|  The id of the role definition which the role assignment is associated with. |
|subjectId|String|  The id of the subject which the role assignment is associated with. |
|linkedEligibleAssignmentId|String|  The id of the linked eliible assignment. If the role assignment is not created by activation, the value is `null`.|
|originId|String| The original id of the resource that is used to identify the resource in the provider.|
|isPermanent|Boolean| Indicates if the role assignment is permanent.|
|startDateTime|DateTimeOffset|The start time of the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|endDateTime|DateTimeOffset|For a non-permanent role assignment, this is the time when the role assignment will be expired. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|assignmentType|String| The type of the assignment. The value can be ``Eligible`` - if it is a *Just in time*  assignment; or ``Member`` - if it is a *direct* assignment or activated from an eligible one.|
|memberType|String|Represents the type of member. The value can be ``Inherited`` - it is inherited from a parent resource scope, ``Group`` - it is not inherited but comes from the membership of a group assignment, or ``User`` - it is not inherited nor from a group assignment.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|linkedEligibleAssignment|[roleAssignment](roleassignment.md)|The linked eligible role assignment. When an eligible role assignment is activated by the user, a member role assignment object will be created in the system. Meanwhile, the member role assignment object will have linkedEligibleAssignment set to the eligible role assignment object.|
|roleDefinition|[roleDefinition](roledefinition.md)|The role definition associated with the role assignment. |
|subject|[subject](subject.md)|The principal subject associated with the role assignment. |

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "resourceId": "String",
  "roleDefinitionId": "String",
  "subjectId": "String",
  "linkedEligibleAssignmentId": "String",
  "originId": "String",
  "isPermanent": true,
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "assignmentType": "String",
  "memberType": "String",
}

```