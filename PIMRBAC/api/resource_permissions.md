# resource: permissions
Returns the caller's current permission levels for the specified resource.

### HTTP request
```http
GET /scenarios('<id>')/resources('<id>')/permissions
```
### Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {code}|

### Request body

### Response
If successful, this method returns `200, OK` response code and [permission](../resources/permission.md) collection object in the response body.

### Example: Get my current permission level for access to subscription "Wingtip Toys - Prod"
##### Request
```http
GET https://graph.microsoft.com/beta/scenarios('pimforrbac')/resources('05a02078-aa1f-482a-8afa-ce1620d03099')/permissions
```

##### Response

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 123

{
  "value": [
    {
      "accessLevel": "AdminRead",
      "isActive": true,
      "isEligible": false
    },
    {
      "accessLevel": "UserRead",
      "isActive": true,
      "isEligible": false
    },
    {
      "accessLevel": "AdminReadWrite",
      "isActive": true,
      "isEligible": false
    }
  ]
}
```