# Get roleSetting

Retrieve the properties and relationships of roleSetting object.
### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /scenarios('<id>')/roleSettings('<id>')
```
### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {code}|
| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|

### Request body
Do not supply a request body for this method.
### Response
If successful, this method returns a `200 OK` response code and [roleSetting](../resources/roleSetting.md) object in the response body.
### Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "get_policy"
}-->
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleSettings('e5e7d29d-5465-45ac-885f-4716a5ee74b5_625c9904-2028-474e-946f-4d7f5b04d24c_5fb5aef8-1081-4b8e-bb16-9d5d0385bab5')
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.policy"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 370

{
  "@odata.context":"https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleSettings$entity","id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_625c9904-2028-474e-946f-4d7f5b04d24c_5fb5aef8-1081-4b8e-bb16-9d5d0385bab5","default":false,"lastUpdated":"2018-02-13T20:07:59.687Z","lastUpdatedBy":"vijag",
  "adminEligibleSettings":[
    {
      "ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":129600}"
    }
  ],
  "adminMemberSettings":[
    {
      "ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":43200}"
    },{
      "ruleIdentifier":"MfaRule","setting":"{\"mfaRequired\":false}"
    },{
      "ruleIdentifier":"JustificationRule","setting":"{\"required\":true}"
    }
  ],
  "userEligibleSettings":[  
  ],
  "userMemberSettings":[
    {
      "ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":480}"
    },{
      "ruleIdentifier":"MfaRule","setting":"{\"mfaRequired\":false}"
    },{
      "ruleIdentifier":"JustificationRule","setting":"{\"required\":true}"
    },{
      "ruleIdentifier":"ApprovalRule","setting":"{\"enabled\":false,\"approvers\":[{\"id\":\"b080efb4-4720-4eca-b103-d507259069e0\",\"displayName\":\"Sankara Srinivas\",\"type\":\"User\",\"email\":\"v-savelp@fimdev.net\"}]}"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get policy",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->