# `roleSetting` entity
Represents a set of rules that will be checked when an administrator tries to add a new role assignment or a user tries to activate his role.



### Methods

| Method		  | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleSetting](../api/roleSetting_list.md) | [roleSetting](roleSetting.md) collection|List roleSetting objects.|
|[Get roleSetting](../api/roleSetting_get.md) |  [roleSetting](roleSetting.md) |Read properties and relationships of roleSetting object.|
|[Update roleSetting](../api/roleSetting_update.md) | [roleSetting](roleSetting.md)	|Update roleSetting object. |

### Properties
| Property	   | Type	|  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| The id of the roleSetting.|
|resourceId|String| The id of the resource that the role setting is associated with.|
|roleDefinitionId|String| The id of the role definition that the role setting is associated with.|
|default|Boolean| Indicate if the roleSetting is a default roleSetting|
|lastUpdated|DateTimeOffset|The time when the role setting was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|lastUpdatedBy|String| The display name of the administrator who last updated the roleSetting.|
|adminEligibleSettings|[ruleSetting](ruleSetting.md) collection|The rule settings that are evaluated when an administrator tries to add an eligible role assignment.|
|adminMemberSettings|[ruleSetting](ruleSetting.md) collection|The rule settings that are evaluated when an administrator tries to add a direct member role assignment.|
|userEligibleSettings|[ruleSetting](ruleSetting.md) collection|The rule settings that are evaluated when a user tries to add an eligible role assignment. This is not used for `pimforrbac` scenario.|
|userMemberSettings|[ruleSetting](ruleSetting.md) collection|The rule settings that are evaluated when a user tries to activate his role assignment.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|resource|[resource](resource.md)| The associated resource for this roleSetting.|
|roleDefinition|[roleDefinition](roledefinition.md)| The role definition that is enforced with this roleSetting. |

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "resourceId": "String",
  "roleDefinitionId": "String",
  "default": true,
  "lastUpdated": "String (timestamp)",
  "lastUpdatedBy": "String",
  "adminEligibleSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "adminMemberSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "userEligibleSettings": [{"@odata.type": "microsoft.graph.rulesetting"}],
  "userMemberSettings": [{"@odata.type": "microsoft.graph.rulesetting"}]
}

```
