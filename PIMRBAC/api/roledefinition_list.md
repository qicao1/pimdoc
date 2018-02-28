# List roleDefinitions

Retrieve a list of roleDefinition objects.

### HTTP request

```http
GET /scenarios('<id>')/roleDefinitions
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
### Example : Get all role definitions for subscription "Wingtip Toys - Prod"
##### Request

```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleDefinitions?$count=true&$expand=resource&$filter=resource/id+eq+'e5e7d29d-5465-45ac-885f-4716a5ee74b5'
```
##### Response
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 227

{  
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#roleDefinitions","@odata.count":75,
  "value":[
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "templateId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "displayName":"Owner",
      "subjectCount":31,
      "activationRequiredCount":29,
      "assignedCount":3
      "resource@odata.context":"https://graph.microsoft.com/beta/$metadata#roleDefinitions('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635')/resource/$entity",
      "resource":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
        "originalId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d",
        "displayName":"Wingtip Toys - Prod",
        "resourceType":"subscription",
        "status":"Active",
        "roleDefinitionCount":0,
        "roleAssignmentCount":0
      }
    },
    ...
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_b24988ac-6180-42a0-ab88-20f7382dd24c",
      "templateId":"b24988ac-6180-42a0-ab88-20f7382dd24c",
      "displayName":"Contributor",
      "subjectCount":16,
      "activationRequiredCount":14,
      "assignedCount":2,
      "resource@odata.context":"https://graph.microsoft.com/beta/$metadata#roleDefinitions('e5e7d29d-5465-45ac-885f-4716a5ee74b5_b24988ac-6180-42a0-ab88-20f7382dd24c')/resource/$entity",
      "resource":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
        "originalId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d",
        "displayName":"Wingtip Toys - Prod",
        "resourceType":"subscription",
        "status":"Active",
        "roleDefinitionCount":0,
        "roleAssignmentCount":0
      }
    }
  ]
}
```