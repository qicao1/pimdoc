# `scenario`

Represents scenarios supported by Privileged Identity Management (PIM), and each scenario defines a group of resources that access could be managed. Those scenarios could be about Azure resources, Azure Active directory, Exchange online, and etc. 

_Note: this version only supports Azure RBAC roles management, thus `pimforrbac` is the only available scenario._

### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[Get scenario](../api/scenario_get.md)| `id` | [scenario](scenario.md) |Read properties and relationships of the scenario object specified by id.|
|[List scenarios](../api/scenario_list.md)| None| [scenario](scenario.md) collection |Read properties and relationships of a list of scenario objects.|


### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String | ✓ | No| Scenario id. Read-only.|
|displayName|String || Yes|The display name of scenario.|


### Relationships
None.
<!--
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|registrations|[tenant](tenant.md) collection|  Read-only. Nullable.|
|activities|[activity](activity.md) collection|  Read-only. Nullable.|
|alerts|[alert](alert.md) collection| Read-only. Nullable.|
|roleSettings|[roleSetting](roleSetting.md) collection|Read-only. Nullable.|
|resources|[resource](resource.md) collection| Read-only. Nullable.|
|roleAssignmentRequests|[roleAssignmentRequest](roleassignmentrequest.md) collection| Read-only. Nullable.|
|roleAssignments|[roleAssignment](roleassignment.md) collection| Read-only. Nullable.|
|roleDefinitions|[roleDefinition](roledefinition.md) collection| Read-only. Nullable.|
-->
### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.provider"
}-->

```json
{
  "id": "String",
  "displayName": "String",
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "provider resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

### Xml representation

```xml
      <EntityType Name="scenario">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="displayName" Type="Edm.String" />
      </EntityType>
```
