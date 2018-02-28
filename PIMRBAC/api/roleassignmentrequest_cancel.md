# Cancel roleAssignmentRequest

Cancel a pending role assignment request.
 
### HTTP request
```http
POST /scenarios('<id>')/roleAssignmentRequests('<id>')/cancel
```

_Note: Only requests that are in status of `Granted`, `PendingApproval` and `PendingAdminDecision` are cancellable._

### Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {code}|

### Request body

### Response
If successful, this method returns `200 OK` response code. It does not return anything in the response body.

### Example
Here is an example of how to call this API.
##### Request
Here is an example of the request.
```http
POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleAssignmentRequests('bc6f10e6-6dd9-4393-853e-09e13c036b17_7fd64851-3279-459b-b614-e2b2ba760f5b_7c53453e-d5a4-41e0-8eb1-32d5ec8bfdee')/cancel
```

##### Response
```http
HTTP/1.1 204 No Content
```