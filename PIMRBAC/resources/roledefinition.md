# `roleDefinition` entity 
Represents the role definitions. 

* For `pimforrbac` scenario, the roleDefinition can represent Azure RBAC roles, such as Owner, Reader, Contributor, etc.


### Methods

| Method		  | Return Type	|Description|
|:---------------|:--------|:--------|:----------|
|[Get roleDefinition](../api/roledefinition_get.md) | [roleDefinition](roledefinition.md) |Read properties and relationships of roleDefinition object.|

### Properties
| Property	   | Type	|  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String|  The id of the role definition. |
|resourceId|String|  The id of the resource associated with the role definition. |
|originId|String| The origin id of the role definition.|
|templateId|String| The template id of the role definition.|
|displayName|String| The display name of the role definition.|
|subjectCount|Int32| The number of subjects that are assigned to the role.|
|activationRequiredCount|Int32|The number of eligible role assignments associated with the role definition.|
|assignedCount|Int32|The number of active role assignments associated with the role definition.|


### Relationships
| Relationship | Type	|Description|
|:---------------|:--------|:----------|
|resource|[resource](resource.md)|The associated resource for the role definition.|
|roleSetting|[roleSetting](rolesetting.md)|The associated role setting for the role definition.|

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "resourceId": "String",
  "originId": "String",
  "templateId": "String",
  "displayName": "String",
  "activationRequiredCount": 1024,
  "assignedCount": 1024,
  "subjectCount": 1024,
}

```