# `scenario` entity

Represents scenarios supported by Privileged Identity Management (PIM), and each scenario defines a group of resources whose access could be managed. Those scenarios could be about Azure resources, Azure Active directory, Exchange online, and etc. 

_Note: this version only supports Azure RBAC roles management, thus `pimforrbac` is the only available scenario._

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String | ✓ | No| Scenario id.|
|displayName|String || Yes|The display name of the scenario.|


### Relationships
None.

### JSON representation

Here is a JSON representation of the resource.

```json
{
  "id": "String (identifier)",
  "displayName": "String",
}
