# `roleDefinition` 
Represents the role definitions. 

For `pimforrbac` scenario, the roleDefinition can represent Azure RBAC roles, such as Owner, Reader, Contributor, etc.


### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List roleDefinitions](../api/roledefinition_list.md) | None | [roleDefinition](roledefinition.md) |Get roleDefinition collection.|
|[Get roleDefinition](../api/roledefinition_get.md) | `id` | [roleDefinition](roledefinition.md) |Read properties and relationships of roleDefinition object.|

<!--
|[Create roleDefinition](../api/resource_post_roledefinitions.md) |  |[roleDefinition](roledefinition.md)| Create a new roleDefinition by posting to the roleDefinitions collection.|
-->


### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓ | No| The id of the role definition. Read-only.|
|templateId|String|   | Yes|The role definition template id that is managed by the resource provider.|
|displayName|String|   | Yes|The role definition display name.|
|subjectCount|Int32|   | Yes|The number of subjects that are assigned with the role.|
|activationRequiredCount|Int32|  | Yes|The number of eligible role assignments associated with the role definition.|
|assignedCount|Int32|   | Yes|The number of member role assignments associated with the role definition.|


### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|resource|[resource](resource.md)|The associated resource for the role definition. Read-only. Nullable.|

### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.roleDefinition"
}-->

```json
{
  "id": "String",
  "templateId": "String",
  "displayName": "String",
  "activationRequiredCount": 1024,
  "assignedCount": 1024,
  "subjectCount": 1024,

}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "roleDefinition resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

### XML representation

```xml
      <EntityType Name="roleDefinition">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="templateId" Type="Edm.String" />
        <Property Name="displayName" Type="Edm.String" />
        <Property Name="subjectCount" Type="Edm.Int32" />
        <Property Name="activationRequiredCount" Type="Edm.Int32" />
        <Property Name="assignedCount" Type="Edm.Int32" />
        <NavigationProperty Name="resource" Type="Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource" ContainsTarget="true" />
      </EntityType>
```