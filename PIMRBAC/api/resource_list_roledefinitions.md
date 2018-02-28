# List roleDefinitions

Get a list of roleDefinition objects for a resource.

### HTTP request
```http
GET /scenarios('<id>')/resources('<id>')/roleDefinitions
```
### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {code}|

### Request body
Do not supply a request body for this method.
### Response
If successful, this method returns a `200 OK` response code and collection of [roleDefinition](../resources/roledefinition.md) objects in the response body.
### Example
#### Get all role definitions of subscription "Wingtip Toys - Prod"
##### Request
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleDefinitions  
```
##### Response
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-Length: 21906

{
    "@odata.context":"https://graph.microsoft.com/beta/$metadata#resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleDefinitions",
    "value":[
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_25cbd04a-2ccf-4ec8-be64-e903c3a1ea91",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"25cbd04a-2ccf-4ec8-be64-e903c3a1ea91",
      "displayName":"Custom Role 3",
      "subjectCount":11,
      "activationRequiredCount":11,
      "assignedCount":0
    },
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_a67ab505-f28a-4d05-919f-e7ba1c9e126c",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"a67ab505-f28a-4d05-919f-e7ba1c9e126c",
      "displayName":"Custom View Role",
      "subjectCount":5,
      "activationRequiredCount":5,
      "assignedCount":0
    },
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_6e450c50-3f8d-4740-a2f5-35032016ae85",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"6e450c50-3f8d-4740-a2f5-35032016ae85",
      "displayName":"Custom View VM Role","subjectCount":1,
      "activationRequiredCount":1,
      "assignedCount":0
    },
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_312a565d-c81f-4fd8-895a-4e21e48d571c",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"312a565d-c81f-4fd8-895a-4e21e48d571c",
      "displayName":"API Management Service Contributor",
      "subjectCount":2,
      "activationRequiredCount":2,
      "assignedCount":0
    },
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_e022efe7-f5ba-4159-bbe4-b44f577e9b61",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"e022efe7-f5ba-4159-bbe4-b44f577e9b61",
      "displayName":"API Management Service Operator Role",
      "subjectCount":0,
      "activationRequiredCount":0,
      "assignedCount":0
    },
    ...
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_de139f84-1756-47ae-9be6-808fbbe84772",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "originId":null,
      "templateId":"de139f84-1756-47ae-9be6-808fbbe84772",
      "displayName":"Website Contributor",
      "subjectCount":1,
      "activationRequiredCount":1,
      "assignedCount":0
    }
  ]
}
```