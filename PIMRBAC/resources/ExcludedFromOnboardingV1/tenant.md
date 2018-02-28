# `tenant` 

Represents an organization or directory in Azure Active Directory.

### Properties
| Property	   | Type	| Key | Nullable |  Description|
|:---------------|:--------|:----------|:--------|:----------|
|id|String| ✓ | No|The tenant id. Read-only.|
|displayName|String| | Yes|The display name of the tenant.|
|initialDomainName| String || Yes|The initial domain name of the tenant.|
|additionalInformation|String|| Yes|The additional information of the tenant.|
|status|String|| Yes|The status of the tenant. The value can be ``Unknown``, ``NotRegisteredYet``, ``RegisteredSetupInProgress``, ``RegistrationAndSetupCompleted``, ``RegistrationFailed``, ``RegistrationTimeout``, ``Disabled``, ``UnregisterStarted``, ``UnregisterInProgress``, and ``UnregisterCompleted``.|

### Relationships
None


### JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tenant"
}-->

```json
{
  "id": "String",
  "displayName": "String",
  "initialDomainName": "String",
  "additionalInformation": "String",
  "status": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "tenant resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

### Xml representation

```xml
      <EntityType Name="tenant">
        <Key>
          <PropertyRef Name="id" />
        </Key>
        <Property Name="id" Type="Edm.String" Nullable="false" />
        <Property Name="displayName" Type="Edm.String" />
        <Property Name="initialDomainName" Type="Edm.String" />
        <Property Name="additionalInformation" Type="Edm.String" />
        <Property Name="status" Type="Edm.String" />
      </EntityType>
```