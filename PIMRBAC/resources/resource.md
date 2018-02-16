# `resource`

Represents resources that could be managed by Privileged Identity Management (PIM). For Azure RBAC scenario, the resource can be a subscription, a resource group, and a resource such as a virtual machine, a SQL database, etc.



### Methods

| Method		  |Input parameters | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[List resources](../api/resource_list.md) | None | [resource](resource.md) |List resource collection.|
|[Get resource](../api/resource_get.md) | `id` | [resource](resource.md) |Read properties and relationships of a resource object specified by id.|
|[List roleAssignments](../api/resource_list_roleassignments.md) |`id` |[roleAssignment](roleassignment.md) collection| Get a roleAssignment object collection for the given resource.|
|[List roleDefinitions](../api/resource_list_roledefinitions.md) |`id` |[roleDefinition](roledefinition.md) collection| Get a roleDefinition object collection for the given resource.|
|[Permissions](../api/resource_permissions.md)|`id` |[permission](permission.md) collection|Get a permission object collection for the given resource and requestor.|

<!--|[Create](../api/resource_update.md) | | [resource](resource.md)	|Create resource object. For Azure RBAC scenario, creating resource is not allowed.| -->

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓ | No|The id of the resource. This is in GUID format. Read-only.|
|displayName| String|| Yes |The resource display name.|
|originalId|String|| Yes|The original id of the resource in its provider. For example, for Azure RBAC scenario, a subscription resource's original id can be /subscriptions/c14ae696-5e0c-4e5d-88cc-bef6637737ac. |
|resourceType|String|| Yes|Resource type. For example, for Azure RBAC provider, the type could be subscription, ResourceGroup, Microsoft.Sql/server, etc.|
|roleAssignmentCount|Int32|| Yes|The number of role assignments for the given resource.|
|roleDefinitionCount|Int32|| Yes|The number of role definitions for the given resource.|
|status|String|| Yes|The status of a given resource. It represents whether the resource is locked. The value can be `Active` and `Locked`.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|alerts|[alert](alert.md) collection| The security alerts that are associated with the resource. Read-only. Nullable.|
|roleAssignments|[roleAssignment](roleassignment.md) collection| The collection of role assignments for the resource. Read-only. Nullable.|
|roleDefinitions|[roleDefinition](roledefinition.md) collection| The collection of role defintions for the resource. Read-only. Nullable.|
|parent|[resource](resource.md) collection| The parent resource. Read-only. Nullable.|

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String",
  "displayName": "String",
  "originalId": "String",
  "resourceType": "String",
  "roleAssignmentCount": 1024,
  "roleDefinitionCount": 1024
}

```

### JSON representation
```xml
      <EntityType Name="resource">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="originalId" Type="Edm.String" />
        <Property Name="displayName" Type="Edm.String" />
        <Property Name="resourceType" Type="Edm.String" />
        <Property Name="status" Type="Edm.String" />
        <Property Name="roleDefinitionCount" Type="Edm.Int32" />
        <Property Name="roleAssignmentCount" Type="Edm.Int32" />
        <NavigationProperty Name="roleDefinitions" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleDefinition)" ContainsTarget="true" />
        <NavigationProperty Name="roleAssignments" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.roleAssignment)" ContainsTarget="true" />
        <NavigationProperty Name="alerts" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.alert)" ContainsTarget="true" />
        <NavigationProperty Name="parent" Type="Collection(Microsoft.Identity.Governance.Common.Data.ExternalModels.V1.resource)" ContainsTarget="true" />
      </EntityType>
```