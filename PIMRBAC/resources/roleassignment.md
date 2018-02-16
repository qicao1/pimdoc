# `roleAssignment` 
Represents the assignment of a role to a user or group.

### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleAssignments](../api/roleassignment_list.md) | None | [roleAssignment](roleassignment.md) |List roleAssignment collection.|
|[Get roleAssignment](../api/roleassignment_get.md) | `id` | [roleAssignment](roleassignment.md) |Read properties and relationships of roleAssignment object.|
|[Export roleAssignment](../api/roleassignment_export.md) | None | octet-stream |Download a list of role assignments and save as a `.csv` file.|

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓  | No| The id of the role assignment. Read-only.|
|originId|String|  | Yes|The original id of the resource that is used to identify the resource in the provider.|
|isPermanent|Boolean|  | Yes|Indicates if the role assignment is permanent.|
|startDateTime|DateTimeOffset|  | Yes|The start time of the role assignment. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|expirationDateTime|DateTimeOffset|  | Yes|For a non-permanent role assignment, this is the time when the role assignment will be expired. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|assignmentType|String|  | Yes|The type of the assignment. The value can be ``Eligible`` - if it is a *Just in time*  assignment; or ``Member`` - if it is a *direct* assignment or activated from an eligible one.|
|membershipType|String| | Yes|Represents the type of membership. The value can be ``Inherited`` - it is inherited from a parent resource scope, ``Group`` - it is not inherited but comes from the membership of a group assignment, or ``User`` - it is not inherited nor from a group assignment.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|linkedAssignment|[roleAssignment](roleassignment.md)|The linked role assignment. When an eligible role assignment is activated by the user, a member role assignment object will be created in the system. Meanwhile, the member role assignment object will have linkedAssignment set to the eligible role assignment object. Read-only. Nullable.|
|roleDefinition|[roleDefinition](roledefinition.md)|The role definition associated with the role assignment. Read-only. Nullable.|
|subject|[subject](subject.md)|The principal subject associated with the role assignment. Read-only. Nullable.|

### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.roleAssignment"
}-->

```json
{
  "id": "String",
  "assignmentType": "String",
  "expirationDateTime": "String (timestamp)",
  "isPermanent": true,
  "level": "String",
  "originId": "String",
  "startDateTime": "String (timestamp)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "roleAssignment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->


 ### XML representation
```xml
      <EntityType Name="roleAssignment">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="originId" Type="Edm.String" />
        <Property Name="isPermanent" Type="Edm.Boolean" />
        <Property Name="expirationDateTime" Type="Edm.DateTimeOffset" />
        <Property Name="startDateTime" Type="Edm.DateTimeOffset" />
        <Property Name="membershipType" Type="Edm.String" />
        <Property Name="assignmentType" Type="Edm.String" />
        <NavigationProperty Name="roleDefinition" Type="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition" ContainsTarget="true" />
        <NavigationProperty Name="subject" Type="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.subject" ContainsTarget="true" />
        <NavigationProperty Name="linkedAssignment" Type="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignment" />
      </EntityType>
```