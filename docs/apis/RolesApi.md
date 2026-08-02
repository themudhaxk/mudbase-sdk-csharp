# Mudbase.SDK.Api.RolesApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AssignRole**](RolesApi.md#assignrole) | **POST** /api/orgs/{orgId}/users/{userId}/role | ~~Assign custom role to user~~ (deprecated) |
| [**CheckPermissions**](RolesApi.md#checkpermissions) | **GET** /api/orgs/{orgId}/users/{userId}/permissions | ~~Check user permissions~~ (deprecated) |
| [**CreateRole**](RolesApi.md#createrole) | **POST** /api/orgs/{orgId}/roles | ~~Create custom role~~ (deprecated) |
| [**DeleteRole**](RolesApi.md#deleterole) | **DELETE** /api/orgs/{orgId}/roles/{roleId} | ~~Delete role~~ (deprecated) |
| [**GetRole**](RolesApi.md#getrole) | **GET** /api/orgs/{orgId}/roles/{roleId} | ~~Get role details~~ (deprecated) |
| [**GetUsersByRole**](RolesApi.md#getusersbyrole) | **GET** /api/orgs/{orgId}/roles/{roleSlug}/users | ~~Get users with specific role~~ (deprecated) |
| [**ListRoles**](RolesApi.md#listroles) | **GET** /api/orgs/{orgId}/roles | ~~List all roles~~ (deprecated) |
| [**RemoveRole**](RolesApi.md#removerole) | **DELETE** /api/orgs/{orgId}/users/{userId}/role | ~~Remove custom role from user~~ (deprecated) |
| [**UpdateRole**](RolesApi.md#updaterole) | **PUT** /api/orgs/{orgId}/roles/{roleId} | ~~Update role~~ (deprecated) |

<a id="assignrole"></a>
# **AssignRole**
> AssignRole200Response AssignRole (string orgId, string userId, AssignRoleRequest assignRoleRequest)

~~Assign custom role to user~~ (deprecated)

Assign a custom role to a user in the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |
| **assignRoleRequest** | [**AssignRoleRequest**](AssignRoleRequest.md) |  |  |

### Return type

[**AssignRole200Response**](AssignRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role assigned successfully |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="checkpermissions"></a>
# **CheckPermissions**
> CheckPermissions200Response CheckPermissions (string orgId, string userId)

~~Check user permissions~~ (deprecated)

Get all permissions for a user (system + custom role combined)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |

### Return type

[**CheckPermissions200Response**](CheckPermissions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User permissions |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createrole"></a>
# **CreateRole**
> CreateRole201Response CreateRole (string orgId, CreateRoleRequest createRoleRequest)

~~Create custom role~~ (deprecated)

Create a new custom role with specific permissions for your organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **createRoleRequest** | [**CreateRoleRequest**](CreateRoleRequest.md) |  |  |

### Return type

[**CreateRole201Response**](CreateRole201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Role created successfully |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deleterole"></a>
# **DeleteRole**
> DeleteRole200Response DeleteRole (string orgId, string roleId)

~~Delete role~~ (deprecated)

Delete a custom role. Cannot delete system roles or roles with active users. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **roleId** | **string** |  |  |

### Return type

[**DeleteRole200Response**](DeleteRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role deleted successfully |  -  |
| **400** | Cannot delete role with active users |  -  |
| **403** | Cannot delete system roles |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getrole"></a>
# **GetRole**
> GetRole200Response GetRole (string orgId, string roleId)

~~Get role details~~ (deprecated)

Get details of a specific custom role. Requires: OrgBearerAuth (organization-level authentication only). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **roleId** | **string** |  |  |

### Return type

[**GetRole200Response**](GetRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role details |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getusersbyrole"></a>
# **GetUsersByRole**
> GetUsersByRole200Response GetUsersByRole (string orgId, string roleSlug)

~~Get users with specific role~~ (deprecated)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **roleSlug** | **string** |  |  |

### Return type

[**GetUsersByRole200Response**](GetUsersByRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of users with this role |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listroles"></a>
# **ListRoles**
> ListRoles200Response ListRoles (string orgId)

~~List all roles~~ (deprecated)

Get all custom roles for the organization. Requires: OrgBearerAuth (organization-level authentication only). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**ListRoles200Response**](ListRoles200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of roles |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="removerole"></a>
# **RemoveRole**
> AssignRole200Response RemoveRole (string orgId, string userId)

~~Remove custom role from user~~ (deprecated)

Remove a custom role from a user in the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |

### Return type

[**AssignRole200Response**](AssignRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Custom role removed successfully |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updaterole"></a>
# **UpdateRole**
> UpdateRole200Response UpdateRole (string orgId, string roleId, UpdateRoleRequest updateRoleRequest)

~~Update role~~ (deprecated)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **roleId** | **string** |  |  |
| **updateRoleRequest** | [**UpdateRoleRequest**](UpdateRoleRequest.md) |  |  |

### Return type

[**UpdateRole200Response**](UpdateRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated successfully |  -  |
| **403** | Cannot modify system roles |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

