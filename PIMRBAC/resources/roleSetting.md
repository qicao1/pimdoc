# `roleSetting` 
Represents the prerequisites that will be checked when an administrator tries to add a new role assignment or a user tries to activate his role.



### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleSetting](../api/roleSetting_list.md) | None | [roleSetting](roleSetting.md) collection|List roleSetting objects.|
|[Get roleSetting](../api/roleSetting_get.md) | `id` | [roleSetting](roleSetting.md) |Read properties and relationships of roleSetting object.|
|[Update](../api/roleSetting_update.md) | `id` | [roleSetting](roleSetting.md)	|Update roleSetting object. |

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓  | No| The id of the roleSetting. Read-only.|
|default|Boolean|  | Yes|Indicate if the roleSetting is a default roleSetting|
|lastUpdated|DateTimeOffset|  | Yes|The time when the roleSetting was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|lastUpdatedBy|String|  | Yes|The display name of the administrator who updated the roleSetting.|
|adminEligibleSettings|[ruleSetting](ruleSetting.md) collection|  | Yes|The rule settings that are evaluated when an administrator tries to add an eligible role assignment.|
|adminMemberSettings|[ruleSetting](ruleSetting.md) collection|  | Yes|The rule settings that are evaluated when an administrator tries to add a direct member role assignment.|
|userEligibleSettings|[ruleSetting](ruleSetting.md) collection|  | Yes|The rule settings that are evaluated when a user tries to add an eligible role assignment. This is not used for Azure RBAC provider.|
|userMemberSettings|[ruleSetting](ruleSetting.md) collection|  | Yes|The rule settings that are evaluated when a user tries to activate his role assignment.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|resource|[resource](resource.md)| The resource that is enforced with this roleSetting. Read-only. Nullable.|
|roleDefinitions|[roleDefinition](roledefinition.md) collection| The role definitions that are enforced with this roleSetting. Read-only. Nullable.|

### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.roleSetting"
}-->

```json
{
  "id": "String",
  "default": true,
  "lastUpdated": "String (timestamp)",
  "lastUpdatedBy": "String",
  "adminEligibleSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "adminMemberSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "userEligibleSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "userMemberSettings": [{"@odata.type": "microsoft.graph.rulesetting"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "roleSetting resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

### XML representation
```XML

      <EntityType Name="roleSetting">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="default" Type="Edm.Boolean" />
        <Property Name="lastUpdated" Type="Edm.DateTimeOffset" />
        <Property Name="lastUpdatedBy" Type="Edm.String" />
        <Property Name="adminEligibleSettings" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.ruleSetting)" />
        <Property Name="adminMemberSettings" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.ruleSetting)" />
        <Property Name="userEligibleSettings" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.ruleSetting)" />
        <Property Name="userMemberSettings" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.ruleSetting)" />
        <NavigationProperty Name="roleDefinitions" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition)" ContainsTarget="true" />
        <NavigationProperty Name="resource" Type="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource" ContainsTarget="true" />
      </EntityType>
```