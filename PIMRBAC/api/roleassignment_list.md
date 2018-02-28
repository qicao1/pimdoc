# List roleAssignments

Retrieve a list of roleassignment objects. 
### HTTP request

```http
GET /scenarios('<id>')/roleAssignments
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
If successful, this method returns a `200 OK` response code and collection of [roleAssignment](../resources/roleassignment.md) objects in the response body.
### Example: Get my role assignments on all resources I have access to
##### Request
To get my role assignments, developers need to explicitly provide `subjectId` in query options.
| Sub scenarios |Query options|
|:----------|:----------|
|Get my eligible role assignment that can be activated| $filter=(linkedEligibleAssignmentId+eq+null+and+assignmentType+eq+'Eligible')|
|Get my active role assignment that can be deactivated| $filter=(linkedEligibleAssignmentId+ne+null+and+assignmentType+eq+'Member')|
|Get my active role assignments| $filter=(assignmentType+eq+'Member')|
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignments?$expand=subject,roleDefinition($expand=resource)&filter=subject/id+eq+'918e54be-12c4-4f4c-a6d3-2ee0e3661c51'
```
##### Response

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-Length: 2062

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#roleAssignments",
  "value":[
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "roleDefinitionId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "subjectId":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
      "linkedEligibleAssignmentId":null,      
      "originId":null,
      "isPermanent":false,
      "endDateTime":"2018-04-02T17:29:00.44Z",
      "startDateTime":"2017-10-04T17:29:18.08Z",
      "assignmentType":"Eligible",
      "memberType":"Direct",
      "subject@odata.context":"https://graph.microsoft.com/beta/$metadata#roleAssignments('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970')/subject/$entity",
      "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User",
        "principalName":"nawu@fimdev.net",
        "email":"nawu@microsoft.com"
      },
      "roleDefinition@odata.context":"https://graph.microsoft.com/beta/$metadata#roleAssignments('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970')/roleDefinition/$entity",
      "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
        "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
        "originId": null,
        "templateId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
        "displayName":"Owner",
        "subjectCount":0,
        "activationRequiredCount":0,
        "assignedCount":0,"resource@odata.context":"https://graph.microsoft.com/beta/$metadata#roleAssignments('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970')/roleDefinition/resource/$entity",
        "resource":{
          "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
          "originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d",
          "displayName":"Wingtip Toys - Prod",
          "type":"subscription",
          "status":"Active",
          "roleDefinitionCount":0,
          "roleAssignmentCount":0
        }
      }
    }
  ]
}
```