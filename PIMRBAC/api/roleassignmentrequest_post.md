# Create roleAssignmentRequest

Use this API to create a new roleAssignmentRequest.
### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /scenarios('<id>')/roleAssignmentRequests
```
### Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {code}|

<!--| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|-->

### Request body
In the request body, supply a JSON representation of [roleAssignmentRequest](../resources/roleassignmentrequest.md) object. Please provide `id` for `roleDefinition`, `resource` and `subject` to uniquely identity a role assignment.

| Property	   | Type	 |  Description|
|:---------------|:--------|:----------|
|id|String|The id of the role assignment request. Use `Guid.Empty` when request and the value will be automatically updated when the request is created successfully;|
|assignmentType|String|The role assignment type. The value can be ``Eligible`` and ``Member``.|
|requestType|String|The request type. The value should be `UserAdd` for activation, `UserRemove` for deactivation, `AdminAdd` for assignment, `AdminRemove` for assignment removal, and `AdminUpdate` for role assignment update, `UserExtend` and `AdminExtend` for extending expiring role assignments.|
|reason|String|The reason needs to be provided for the role assignment request for audit and review purpose.|
|evaluateOnly|Boolean|Indicates if the API call is for evaluation purpose only.|
|schedule|[schedule](schedule.md)| The schedule of the role assignment request. For request type of `UserAdd`, `AdminAdd`, `AdminUpdate`, and `AdminExtend`, it is required.|

### Response
If successful, this method returns `201, Created` response code and [roleAssignmentRequest](../resources/roleassignmentrequest.md) object in the response body.

### Example
##### Request
Here is an example of the request that a user tries to activate his eligible role assignment.
<!-- {
  "blockType": "request",
  "name": "create_roleassignmentrequest_from_roleassignmentrequests"
}-->
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests
Content-type: application/json
Content-length: 206

{
    "id": "00000000-0000-0000-0000-000000000000",
    "roleDefinition": 
    {
        "id": "8575d82b-c7b6-4c69-8fff-1d452985a64e_7fd64851-3279-459b-b614-e2b2ba760f5b",
        "displayName": "Office DevOps",
        "resource": { "id": "8575d82b-c7b6-4c69-8fff-1d452985a64e" }
    },
    "subject": 
    {
        "id": "795ed4a8-e4e5-48f5-b60c-ee9845a7a790",
        "displayName": "admin1",
        "type": "User"
    },
    "assignmentType": "Member",
    "requestType": "UserAdd",
    "reason": "activate me",
    "schedule": 
    {
        "type": "Once",
        "startDateTime": "2017-10-04T17:42:56.841Z",
        "duration": "PT8H"
    },
    "evaluateOnly": false
}
```

In the request body, supply a JSON representation of [roleAssignmentRequest](../resources/roleassignmentrequest.md) object.
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.roleAssignmentRequest"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 226

{
    "@odata.context": "https://api.azrbac.mspim.azure.com/api/v1/$metadata#roleAssignmentRequests/$entity",
    "id": "8575d82b-c7b6-4c69-8fff-1d452985a64e_7fd64851-3279-459b-b614-e2b2ba760f5b_b59f5fba-a6a9-4ac4-9715-30aaa50516bc",
    "assignmentType": "Member",
    "requestType": "UserAdd",
    "requestedDateTime": "0001-01-01T00:00:00Z",
    "roleAssignmentStartDateTime": "2017-10-04T17:42:56.841Z",
    "status": "Granted",
    "reason": "active",
    "statusDetail": [
        {
            "key": "EligibilityRule",
            "value": "Grant"
        },
        {
            "key": "ExpirationRule",
            "value": "Grant"
        },
        {
            "key": "MfaRule",
            "value": "Grant"
        },
        {
            "key": "JustificationRule",
            "value": "Grant"
        },
        {
            "key": "ActivationDayRule",
            "value": "Grant"
        },
        {
            "key": "ApprovalRule",
            "value": "Grant"
        }
    ],
    "schedule": {
        "duration": "PT8H",
        "type": "Once",
        "details": null,
        "startDateTime": "2017-10-04T17:42:56.841Z",
        "isPermanent": false,
        "stopDateTime": "0001-01-01T00:00:00Z"
    },
    "targetLinkedRoleAssignmentId": null,
    "evaluateOnly": false
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create roleAssignmentRequest",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->