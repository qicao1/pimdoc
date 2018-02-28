# Update roleSetting
Update the properties of roleSetting object.

### HTTP request

```http
PUT /scenarios('<id>')/roleSettings('<id>')
```
### Optional request headers
| Name       | Description|
|:-----------|:-----------|
| Authorization  | Bearer {code}|


### Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. 

| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|id|String|The id of the role setting.|
|adminEligibleSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when an administrator tries to add an eligible role assignment.|
|adminMemberSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when an administrator tries to add a direct member role assignment.|
|isDefault|Boolean|Indicate if the roleSetting is a default roleSetting.|
|lastUpdated|DateTimeOffset|The time when the roleSetting was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'.|
|lastUpdatedBy|String|The display name of the administrator who updated the roleSetting.|
|userEligibleSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when a user tries to add an eligible role assignment. This is not used for `pimforrbac` scenario.|
|userMemberSettings|[ruleSetting](../resources/ruleSetting.md)|The rule settings that are evaluated when a user tries to activate his role assignment.|

### Response
If successful, this method returns a `204 No Cotent` response code.
### Example : Update role setting for "Custom Role 3" in subscription "Wingtip Toys - Prod"
##### Request

```http
PUT https://graph.microsoft.com/beta/scenarios('pimforrbac')/roleSettings('e5e7d29d-5465-45ac-885f-4716a5ee74b5_625c9904-2028-474e-946f-4d7f5b04d24c_5fb5aef8-1081-4b8e-bb16-9d5d0385bab5')
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