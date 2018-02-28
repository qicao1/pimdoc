# Featured scenarios 
Here are a list of featured scenarios in PIM for Azure RBAC roles.

| Scenario      | URL|
|:-----------|:-----------|
| Administrators assign a user to a role | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Administrators remove a user from a role | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)  
| Administrators update a role assignment| [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Administrators approve a request to extend role assignment | [PUT https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests('\<id\>')/updateAdminDecision](api/roleassignmentrequest_updateadmindecision.md) |
| Administrators list role settings on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings?$expand=resource&$filter=(resource/id+eq+'\<id\>')](api/rolesetting_list.md)|
| Administrators get a single role setting| [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings('\<id\>')](api/rolesetting_get.md)|
| Administrators update role settings for a role | [PUT https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings('\<id\>')](api/rolesetting_update.md) |
| list all resources I have access to | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources](api/resource_list.md) |
| Get details of a single resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')](api/resource_get.md) |
| List all child resources of a subscription | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources?$filter=(type+ne+'subscription')](api/resource_list.md) |
| List role definitions on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/roleDefinitions](api/resource_list_roledefinitions.md)|
| List role assignments on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/roleAssignments](api/resource_list_roleassignments.md)<br/>[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments?$expand=resource&$filter=resource/id+eq+'\<id\>'](api/roleassignment_list.md)|
| Get my current access levels for a resource |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/permissions](api/resource_permissions.md) |
| Get a single role definition |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleDefinitions('\<id\>')](api/roledefinition_get.md) |
| Get a single role assignment |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments('\<id\>')](api/roleassignment_get.md) |
| List my role assignments on all resources I have access to | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments?$expand=linkedEligibleAssignment,subject,roleDefinition($expand=resource)]((api/roleassignment_list.md)) |
| Activate an eligible role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)|
| Deactivate an active role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Extends an expiring role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)|
| Cancel a pending role assignment request| [POST https://graph.microsoft.com/beta/scenarios('pimforrbac')/cancel](api/roleassignmentrequest_cancel.md)  |
