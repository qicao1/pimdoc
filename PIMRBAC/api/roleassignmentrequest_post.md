# Create roleAssignmentRequest

Use this API to create a new roleAssignmentRequest, including:
*   Administrators assign a user or group to a role;
*   Administrators update a role assignment;
*   Administrators remove a user or group from a role;
*   Administrators extend an expiring role assignment;
*   Users activate an eligible role assignment;
*   Users deactivate an active role assignment;
*   Users request to extend an expiring role assignment;
 
### HTTP request
```http
POST /scenarios('<id>')/roleAssignmentRequests
```
### Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {code}|

### Request body
In the request body, supply a JSON representation of [roleAssignmentRequest](../resources/roleassignmentrequest.md) object. Please provide `id`s for `roleDefinition`, `resource` and `subject` to uniquely identity a role assignment.

| Property	   | Type	 |  Description|
|:---------------|:--------|:----------|
|id|String|The id of the role assignment request. Use `Guid.Empty` when request and the value will be automatically updated when the request is created successfully;|
|assignmentType|String|The role assignment type. The value can be ``Eligible`` and ``Member``.|
|type|String|The request type. The value can be <ul><li>`AdminAdd`: An adminstrator assign a user or group to a role;</li><li>`UserAdd`: A user activate his eligible role assignment;</li><li> `AdminUpdate`: An adminstrator changes existing role assignments</li><li>`AdminRemove`: An adminstrator removes a user or group from a role;<li>`UserRemove`: a user deactivate an active role assignment;<li>`UserExtend`: a user requests to extend expiring role assignments;</li><li>`AdminExtend`: an administrator extends an expiring role assignment for a user or group.</li></ul>|
|reason|String|The reason needs to be provided for the role assignment request for audit and review purpose.|
|evaluateOnly|Boolean|Indicates if the API call is for evaluation purpose only.|
|schedule|[schedule](schedule.md)| The schedule of the role assignment request. For request type of `UserAdd`, `AdminAdd`, `AdminUpdate`, and `AdminExtend`, it is required.|

### Response
If successful, this method returns `201, Created` response code and [roleAssignmentRequest](../resources/roleassignmentrequest.md) object in the response body.

### Example
#### 1. Administrators assign user "nawu@fimdev.net" to role "Billing Reader"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206
{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "displayName":"Billing Reader",
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
   },
   "subject":{
       "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
       "displayName":"nawu",
       "type":"User"
    },
    "assignmentType":"Eligible",
    "type":"AdminAdd",
    "reason":null,
    "schedule":{
        "type":"Once","startDateTime":"2018-02-28T08:22:13.840Z","endDateTime":"2018-05-29T08:22:13.840Z","isPermanent":false
    },
    "evaluateOnly":false
}
```
##### Response

```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_02e516e5-224c-4035-95f4-6a896cbdb4a8",
  "resourceId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5",
  "roleDefinitionId":"fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64",
  "subjectId":"02e516e5-224c-4035-95f4-6a896cbdb4a8",  
  "assignmentType":"Eligible",
  "type":"AdminAdd",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":"2018-02-28T08:22:38.3569224Z",
  "status":"Granted",
  "reason":null,
  "statusDetail":[
    {
      "key":"AdminRequestRule","value":"Grant"
    },{
      "key":"ExpirationRule","value":"Grant"
    },{
      "key":"MfaRule","value":"Grant"
    }
  ],
  "schedule":{
    "duration":"PT0S",
    "type":"Once",
    "details":null,"startDateTime":"2018-02-28T08:22:13.84Z","isPermanent":false,"endDateTime":"2018-05-29T08:22:13.84Z"
  },
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```

#### 2. User "nawu@fimdev.net" activate the eligible role "Billing Reader"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206
{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64",
        "displayName":"Billing Reader",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
    },
    "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User"
    },
    "assignmentType":"Member",
    "type":"UserAdd",
    "reason":"test",
    "schedule":{
        "type":"Once",
        "startDateTime":"2018-02-28T08:32:50.884Z",
        "duration":"PT8H"
    },"targetLinkedRoleAssignmentId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_c35cd26c-c43f-4f62-af6b-5d2c0933a5af",
    "evaluateOnly":false
    }
```
##### Response

```json
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://canaryapi.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_3905f617-b4c3-489a-8c31-72d96dfaf9dc",
  "assignmentType":"Member",
  "requestType":"UserAdd",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":"2018-02-28T08:33:15.8489422Z",
  "status":"PendingApprovalProvisioning",
  "reason":"test",
  "statusDetail":[
    {
      "key":"EligibilityRule","value":"Grant"
    },{
      "key":"ExpirationRule","value":"Grant"
    },{
      "key":"MfaRule","value":"Grant"
    },{
      "key":"JustificationRule","value":"Grant"
    },{
      "key":"ActivationDayRule","value":"Grant"
    },{
      "key":"ApprovalRule","value":"Defer"
    }
  ],
  "schedule":{
    "duration":"PT8H",
    "type":"Once",
    "details":null,"startDateTime":"2018-02-28T08:32:50.884Z","isPermanent":false,
    "endDateTime":"0001-01-01T00:00:00Z"
  },
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```

#### 3. User "nawu@fimdev.net" deactivate the active role "Billing Reader"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206

{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
    },
    "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "type":"User"
    },
    "assignmentType":"Member",
    "type":"UserRemove",
    "reason":"Deactivation request",
    "schedule":null,"targetLinkedRoleAssignmentId":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_918e54be-12c4-4f4c-a6d3-2ee0e3661c51_ebd33f32-2c4b-457b-95c4-f07c3a39e3cb",
    "evaluateOnly":false
}
```
##### Response

```json
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://canaryapi.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_44e535c7-9e8d-480b-908f-2cf3281a87ea",
  "assignmentType":"Member",
  "type":"UserRemove",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":null,
  "status":"Revoked","
  reason":"Deactivation request",
  "statusDetail":[],
  "schedule":null,
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```

#### 4. Administrators remove user "nawu@fimdev.net" from role "Billing Reader"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206

{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64",
        "displayName":"Billing Reader",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
    },
    "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User",
        "principalName":"nawu@fimdev.net","email":"nawu@microsoft.com"
    },
    "assignmentType":"Eligible",
    "type":"AdminRemove",
    "reason":null,
    "schedule":null,
    "evaluateOnly":false
}
```
##### Response

```json
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://canaryapi.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_fa23ad8b-c56e-40d8-ac0c-ce449e1d2c64_f442ff7d-5480-439d-8dbc-f5aac2682fd4",
  "assignmentType":"Eligible",
  "type":"AdminRemove",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":null,
  "status":"Revoked",
  "reason":null,
  "statusDetail":[],
  "schedule":null,
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```

#### 5. Administrators update role assignment for user "nawu@fimdev.net" to role "Owner"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206

{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635",
        "displayName":"Owner",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
    },
    "subject":{
        "id":"918e54be-12c4-4f4c-a6d3-2ee0e3661c51",
        "displayName":"nawu",
        "type":"User",
        "principalName":"nawu@fimdev.net","email":"nawu@microsoft.com"
        },
    "assignmentType":"Eligible",
    "type":"AdminUpdate",
    "reason":"",
    "schedule":{
        "type":"Once",
        "startDateTime":"2017-10-04T17:29:18.080Z","endDateTime":"2018-04-01T17:29:00.000Z","isPermanent":false
    },
    "evaluateOnly":false
}
```
##### Response

```json
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://canaryapi.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_8e3af657-a8ff-443c-a75c-2fe8c4bcb635_d210be67-d702-416d-a6b2-2494d10c60d2",
  "assignmentLevel":"Eligible",
  "type":"AdminUpdate",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":"2018-02-28T08:55:15.869694Z",
  "status":"Granted",
  "reason":"",
  "statusDetail":[
    {
      "key":"AdminRequestRule","value":"Grant"
    },{
      "key":"ExpirationRule","value":"Grant"
    },{
      "key":"MfaRule","value":"Grant"
    }
  ],
  "schedule":{
    "duration":"PT0S",
    "type":"Once",
    "details":null,
    "startDateTime":"2017-10-04T17:29:18.08Z",
    "isPermanent":false,
    "endDateTime":"2018-04-01T17:29:00Z"
  },
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```

#### 6. Extend expiring role assignment for user ANUJCUSER to role "API Management Service Contributor"
##### Request
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206

{
    "id":"00000000-0000-0000-0000-000000000000",
    "roleDefinition":{
        "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_312a565d-c81f-4fd8-895a-4e21e48d571c",
        "resource":{
            "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5"
        }
    },
    "subject":{
        "id":"74487eb5-1630-4fa8-9581-0bb076ea5de3"
    },
    "assignmentType":"Eligible",
    "requestType":"AdminExtend",
    "reason":"try extend",
    "evaluateOnly":false
}
```
##### Response

```json
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226
{
  "@odata.context":"https://canaryapi.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_312a565d-c81f-4fd8-895a-4e21e48d571c_d976ab01-e425-44b5-b475-7c12d9fe9c7a",
  "assignmentType":"Eligible",
  "type":"AdminExtend",
  "requestedDateTime":"0001-01-01T00:00:00Z",
  "roleAssignmentStartDateTime":"2018-02-28T09:03:34.168707Z",
  "status":"Granted",
  "reason":"try extend",
  "statusDetail":[
    {
      "key":"AdminRequestRule","value":"Grant"
    },{
      "key":"ExpirationRule","value":"Grant"
    },{
      "key":"MfaRule","value":"Grant"
    }
  ],
  "schedule":{
    "duration":"P90D",
    "type":"Once",
    "details":null,
    "startDateTime":"0001-01-01T00:00:00Z",
    "isPermanent":false,
    "stopDateTime":"0001-01-01T00:00:00Z"
  },
  "targetLinkedRoleAssignmentId":null,
  "evaluateOnly":false
}
```