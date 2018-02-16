# Update roleSetting
Update the properties of roleSetting object.
### Prerequisites
The following **scopes** are required to execute this API: 
### HTTP request
<!-- { "blockType": "ignored" } -->
```http
PUT /scenarios('<id>')/roleSettings('<id>')
```
### Optional request headers
| Name       | Description|
|:-----------|:-----------|
| Authorization  | Bearer {code}|
| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|

### Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|adminEligibleSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when an administrator tries to add an eligible role assignment.|
|adminMemberSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when an administrator tries to add a direct member role assignment.|
|default|Boolean||
|lastUpdated|DateTimeOffset||
|lastUpdatedBy|String||
|userEligibleSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when a user tries to add an eligible role assignment. This is not used for `pimforrbac` scenario.|
|userMemberSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when a user tries to activate his role assignment.|

### Response
If successful, this method returns a `204 No Cotent` response code.
### Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "update_policy"
}-->
```http
PUT https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleSettings('<id>')
Content-type: application/json
Content-length: 350

{
  "id":"e5e7d29d-5465-45ac-885f-4716a5ee74b5_625c9904-2028-474e-946f-4d7f5b04d24c_5fb5aef8-1081-4b8e-bb16-9d5d0385bab5",
  "adminEligibleSettings":[{"ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":129600}"}],
  "adminMemberSettings":[{"ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":43200}"},{"ruleIdentifier":"MfaRule","setting":"{\"mfaRequired\":false}"},{"ruleIdentifier":"JustificationRule","setting":"{\"required\":true}"}],
  "userEligibleSettings":[],
  "userMemberSettings":[{"ruleIdentifier":"ExpirationRule","setting":"{\"permanentAssignment\":false,\"maximumGrantPeriodInMinutes\":540}"},{"ruleIdentifier":"MfaRule","setting":"{\"mfaRequired\":false}"},{"ruleIdentifier":"JustificationRule","setting":"{\"required\":true}"},{"ruleIdentifier":"ApprovalRule","setting":"{\"enabled\":false,\"approvers\":[{\"id\":\"b080efb4-4720-4eca-b103-d507259069e0\",\"displayName\":\"Sankara Srinivas\",\"type\":\"User\",\"email\":\"v-savelp@fimdev.net\"}]}"}]
}
```
##### Response
None.