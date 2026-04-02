# Mudbase.SDK.Api.IntegrationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**IntegrationsExecute**](IntegrationsApi.md#integrationsexecute) | **POST** /api/integrations/projects/{projectId}/integrations/{integrationId}/execute | Execute integration |
| [**IntegrationsList**](IntegrationsApi.md#integrationslist) | **GET** /api/integrations/projects/{projectId}/integrations | Get project integrations |

<a id="integrationsexecute"></a>
# **IntegrationsExecute**
> MultiRoleGetPermissionsMatrix200Response IntegrationsExecute (string projectId, string integrationId, IntegrationsExecuteRequest integrationsExecuteRequest)

Execute integration

Execute an integration action (API call) with specified endpoint and parameters. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **integrationId** | **string** | Integration ID to execute. |  |
| **integrationsExecuteRequest** | [**IntegrationsExecuteRequest**](IntegrationsExecuteRequest.md) | Endpoint path, HTTP method, optional params and body for the integration call. |  |

### Return type

[**MultiRoleGetPermissionsMatrix200Response**](MultiRoleGetPermissionsMatrix200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration executed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="integrationslist"></a>
# **IntegrationsList**
> IntegrationsList200Response IntegrationsList (string projectId)

Get project integrations

List all integrations configured for a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |

### Return type

[**IntegrationsList200Response**](IntegrationsList200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integrations list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

