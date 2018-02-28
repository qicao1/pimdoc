# `resource` entity

Represents resources that could be managed by Privileged Identity Management (PIM). 
* For `pimforrbac` scenario, the resource can be a subscription, a resource group, and a resource such as a virtual machine, a SQL database, etc.



### Methods

| Method		  | Return Type	|Description|
|:---------------|:--------|:----------|
|[List resources](../api/resource_list.md) | [resource](resource.md) |List resource collection.|
|[Get resource](../api/resource_get.md) | [resource](resource.md) |Read properties and relationships of a resource object specified by id.|
|[List roleAssignments](../api/resource_list_roleassignments.md)  |[roleAssignment](roleassignment.md) collection| Get a roleAssignment object collection for the given resource.|
|[List roleDefinitions](../api/resource_list_roledefinitions.md)  |[roleDefinition](roledefinition.md) collection| Get a roleDefinition object collection for the given resource.|
|[Permissions](../api/resource_permissions.md) |[permission](permission.md) collection|Get a permission object collection for the given resource and requestor.|

### Properties
| Property	   | Type	|   Description|
|:---------------|:--------|:----------|
|id|String| The id of the resource. This is in GUID format.|
|originId|String|The origin id of the resource. For example, for `pimforrbac` scenario, a subscription resource's origin id can be "/subscriptions/c14ae696-5e0c-4e5d-88cc-bef6637737ac". |
|type|String|Resource type. For example, for `pimforrbac` scenario, the type could be "Subscription", "ResourceGroup", "Microsoft.Sql/server", etc.|
|displayName| String|The display name of the resource.|
|roleAssignmentCount|Int32|The number of role assignments for the given resource.|
|roleDefinitionCount|Int32|The number of role definitions for the given resource.|
|status|String|The status of a given resource. It represents whether the resource is locked or not. The value can be `Active` or `Locked`.|

### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|roleAssignments|[roleAssignment](roleassignment.md) collection| The collection of role assignments for the resource.|
|roleDefinitions|[roleDefinition](roledefinition.md) collection| The collection of role defintions for the resource.|
|parent|[resource](resource.md) collection| The parent resource. for `pimforrbac` scenario, it represents the subscription the resource belongs to.|

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "originId": "String",
  "type": "String",
  "displayName": "String",
  "roleAssignmentCount": 1024,
  "roleDefinitionCount": 1024,
  "status": "String"
}

```