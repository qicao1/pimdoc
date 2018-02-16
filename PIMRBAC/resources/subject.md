# `subject` type
Represents users, groups, and service principals being managed in Privileged Identity Management (PIM).


### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id| String|✓ | No| Identifier. The subject id. Read-only.|
|displayName|String| | Yes|Subject display name.|
|email|String| | Yes|The subject's email.|
|principalName|String| | Yes|The principal name of the subject. |
|type|String| | Yes|The type of the subject. The value can be ``User``, ``Group``, ``ServicePrincipal``, ``GroupSecurityNotEnabled``, and ``Role``.|

### Relationships
None


### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.subject"
}-->

```json
{
  "id": "String",  
  "displayName": "String",
  "email": "String",
  "principalName": "String",
  "type": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "subject resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

### XML representation
```xml
      <EntityType Name="subject">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="displayName" Type="Edm.String" />
        <Property Name="type" Type="Edm.String" />
        <Property Name="principalName" Type="Edm.String" />
        <Property Name="email" Type="Edm.String" />
      </EntityType>
```