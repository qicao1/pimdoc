# List roleAssignments

Retrieve a list of roleassignment objects.
### HTTP request
```http
GET /scenarios('<id>')/resources('<id>')/roleAssignments
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
### Examples
#### 1. Get my role assignments in subscription "Wingtip Toys - Prod"
##### Request
To get my role assignments, developers need to explicitly provide `subjectId` in query options.
| Sub scenarios |Query options|
|:----------|:----------|
|Get my eligible role assignment that can be activated| $filter=(linkedEligibleAssignmentId+eq+null+and+assignmentType+eq+'Eligible')|
|Get my active role assignment that can be deactivated| $filter=(linkedEligibleAssignmentId+ne+null+and+assignmentType+eq+'Member')|
|Get my active role assignments| $filter=(assignmentType+eq+'Member')|


```http
GET  https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments?$expand=linkedEligibleAssignment,subject&$filter=(subject/id+eq+'918e54be-12c4-4f4c-a6d3-2ee0e3661c51')
```
##### Response
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-Length: 2353
{     
    "@odata.context":"https://graph.microsoft.com/beta/$metadata#resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments",
    "value":[
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "roleDefinitionId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "subjectId":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
      "linkedEligibleAssignmentId":null,
      "originId":null,
      "isPermanent":false,
      "startDateTime":"2017-10-04T17:29:18.08Z",
      "endDateTime":"2018-04-02T17:29:00.44Z",
      "assignmentType":"Eligible",
      "memberType":"Direct",
      "linkedEligibleAssignment":null,
      "subject@odata.context":"https://graph.microsoft.com/beta/$metadata#resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970')/subject/$entity",
      "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User",
        "principalName":"nawu@fimdev.net",
        "email":"nawu@microsoft.com"
      }
    },
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_b8b14bf8-08d0-47ac-b008-a728b43d4d46",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "roleDefinitionId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "subjectId":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
      "linkedEligibleAssignmentId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_2d8bb67d-c8e8-4a89-9a60-3ddf6545c970",
      "originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/providers/Microsoft.Authorization/roleAssignments/b8b14bf8-08d0-47ac-b008-a728b43d4d46",
      "isPermanent":false,
      "endDateTime":"2018-02-28T01:40:15.38Z",
      "startDateTime":"2018-02-27T20:40:17.977Z",
      "assignmentType":"Member",
      "memberType":"Direct",
      "linkedEligibleAssignment":{
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
        "memberType":"Direct"
      },
      "subject@odata.context":"https://graph.microsoft.com/beta/$metadata#resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments('e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_b8b14bf8-08d0-47ac-b008-a728b43d4d46')/subject/$entity",
      "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User",
        "principalName":"nawu@fimdev.net",
        "email":"nawu@microsoft.com"
      }
    }
  ]
}
```
#### 2. Administrator gets all active role assignments in subscription "Wingtip Toys - Prod"

| Sub scenarios |Query options|
|:----------|:----------|
|Get eligible role assignment that can be activated| $filter=(linkedEligibleAssignmentId+eq+null+and+assignmentType+eq+'Eligible')|
|Get active role assignment that can be deactivated| $filter=(linkedEligibleAssignmentId+ne+null+and+assignmentType+eq+'Member')|
|Get active role assignments| $filter=(assignmentType+eq+'Member')|

```http
GET  https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments
```
##### Response
```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 48609

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#resources('e5e7d29d-5465-45ac-885f-4716a5ee74b5')/roleAssignments",
  "value":[
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_74487eb5-1630-4fa8-9581-0bb076ea5de3_0ba78f41-ee7a-4227-adb9-1499431b2164",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "roleDefinitionId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "subjectId":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
      "linkedEligibleAssignmentId":null,
      "originId":null,
      "isPermanent":false,
      "endDateTime":"2018-07-21T23:47:02.887Z",
      "startDateTime":"2018-01-22T23:47:19.687Z",
      "assignmentType":"Eligible",
      "memberType":"Direct"
    },
    ...
    {
      "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_7dbe47c0-656b-445a-95a7-12f23dbdcb57_1206372a-91cb-4cd6-a3e8-eb8877938232",
      "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
      "roleDefinitionId":"8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
      "subjectId":"7dbe47c0-656b-445a-95a7-12f23dbdcb57",
      "linkedEligibleAssignmentId":null,
      "originId":null,
      "isPermanent":false,
      "endDateTime":"2018-04-02T17:27:45.417Z",
      "startDateTime":"2017-10-04T17:27:58.857Z",
      "assignmentType":"Eligible",
      "memberType":"Direct"
    }
  ]
}
```