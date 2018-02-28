# Featured scenarios 
Here are a list of featured scenarios in PIM for Azure RBAC roles.

## 1. Discovery of resources, role definitions, role assignments, role settings, and role assignment requests
| Scenario      | URL|
|:----------|:-----------|
| List all resources I have access to | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources](api/resource_list.md) |
| Get details of a single resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')](api/resource_get.md) |
| List role definitions on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/roleDefinitions](api/resource_list_roledefinitions.md)|
| List role assignments on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/roleAssignments](api/resource_list_roleassignments.md)<br/>[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments?$expand=resource&$filter=resource/id+eq+'\<id\>'](api/roleassignment_list.md)|
| Get my current access levels for a resource |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/resources('\<id\>')/permissions](api/resource_permissions.md) |
| Get a single role definition |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleDefinitions('\<id\>')](api/roledefinition_get.md) |
| Get a single role assignment |[GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments('\<id\>')](api/roleassignment_get.md) |
| List my role assignments on all resources I have access to | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignments?$expand=linkedEligibleAssignment,subject,roleDefinition($expand=resource)]((api/roleassignment_list.md)) |

## 2. Administrator management
| Scenario      | URL|
|:-----------|:-----------|
| Assign a user to a role | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Remove a user from a role | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)  
| Update a role assignment| [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Approve or deny a request to extend role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests('\<id\>') /updateAdminDecision](api/roleassignmentrequest_updateadmindecision.md) |
| List role settings on a resource | [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings?$expand=resource&$filter=(resource/id+eq+'\<id\>')](api/rolesetting_list.md)|
| Get a single role setting| [GET https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings('\<id\>')](api/rolesetting_get.md)|
| Update role settings for a role | [PUT https://graph.microsoft.com/beta/scenarios('\<id\>')/roleSettings('\<id\>')](api/rolesetting_update.md) |

## 3. User operations on role assignments
| Scenario      | URL|
|:-----------|:-----------|
| Activate an eligible role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)|
| Deactivate an active role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md) |
| Extend an expiring role assignment | [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/roleAssignmentRequests](api/roleassignmentrequest_post.md)|
| Cancel a pending role assignment request| [POST https://graph.microsoft.com/beta/scenarios('\<id\>')/cancel](api/roleassignmentrequest_cancel.md)  |
