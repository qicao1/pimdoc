# List resources

Retrieve a list of resource objects the requestor has access to.

### HTTP request
```http
GET /scenarios('<id>')/resources
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
If successful, this method returns a `200 OK` response code and collection of [resource](../resources/resource.md) objects in the response body.
### Examples

#### 1. List all resources I can currently access to
##### Request
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources
```
##### Response

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-Length: 1289

{
	"@odata.context":"https://graph.microsoft.com/beta/$metadata#resources",
	"value":[
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('ee33e978-dc0b-40ee-9db3-fb9a0dae41e8')",
	"id":"ee33e978-dc0b-40ee-9db3-fb9a0dae41e8",
	"originId":"/subscriptions/c14ae696-5e0c-4e5d-88cc-bef6637737a0",
	"type":"subscription",
	"displayName":"Microsoft Azure Internal Consumption",
	"roleDefinitionCount":59,
	"roleAssignmentCount":23,
	"status":"Active"
 	},
 	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('93b5660d-a79a-40fc-951f-88ef2eac2608')",
	"id":"93b5660d-a79a-40fc-951f-88ef2eac2608",
	"originId":"/subscriptions/20d27ca6-0bc7-4396-bc31-be959acf3d46",
	"type":"subscription",
	"displayName":"Subscription for debac@microsoft.com",
	"roleDefinitionCount":59,
	"roleAssignmentCount":13,
	"status":"Active"
	},
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('300c6d07-f908-46d4-b4c2-307f786a9832')",
	"id":"300c6d07-f908-46d4-b4c2-307f786a9832",
	"originId":"/subscriptions/ad5b7423-de55-4d5c-b604-f5806571b3c1",
	"type":"subscription",
	"displayName":"Subscription5 for anujc@microsoft.com",
	"roleDefinitionCount":59,
	"roleAssignmentCount":11,
	"status":"Active"
	}]
}
```
#### 2. List resources with odata query options: list all resource groups in a subscription
##### Request
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources?$orderby=displayName&$filter=(type+eq+'resourcegroup')
```
##### Response

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 247

{
	"@odata.context":"https://graph.microsoft.com/beta/$metadata#resources",
	"value":[
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('ad732914-e7d3-45d2-98cb-f491ba40e556')",	
	"id":"ad732914-e7d3-45d2-98cb-f491ba40e556",	
	"originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/AnujRG",
	"displayName":"AnujRG",
	"type":"resourcegroup",
	"status":"Active",
	"roleDefinitionCount":75,
	"roleAssignmentCount":16
	},
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('8c623aba-6ceb-486e-bdfd-fd1156570ce9')",	
	"id":"8c623aba-6ceb-486e-bdfd-fd1156570ce9",	
	"originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/ARPJ-TESTRG-01",
	"displayName":"ARPJ-TESTRG-01",
	"type":"resourcegroup",
	"status":"Active",
	"roleDefinitionCount":75,
	"roleAssignmentCount":15
	},
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('75a768ce-c80a-4e38-b691-f2411b5e090e')",	
	"id":"75a768ce-c80a-4e38-b691-f2411b5e090e",	
	"originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/cloud-shell-storage-westus",	
	"displayName":"cloud-shell-storage-westus",	
	"type":"resourcegroup",
	"status":"Active",
	"roleDefinitionCount":75,
	"roleAssignmentCount":14
	},
	{
	"@odata.id":"https://graph.microsoft.com/beta/resources('4e3f2694-0cfa-4292-8897-6f8dc35f2729')",
	"id":"4e3f2694-0cfa-4292-8897-6f8dc35f2729",	
	"originId":"/subscriptions/38ab2ccc-3747-4567-b36b-9478f5602f0d/resourceGroups/dashboards",
	"displayName":"dashboards",
	"type":"resourcegroup",
	"status":"Active",
	"roleDefinitionCount":75,
	"roleAssignmentCount":14
	}
	],
	"@odata.nextLink":"https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources?$orderby=displayName&$filter=type+eq+'resourcegroup'&$skip=10"
}
```