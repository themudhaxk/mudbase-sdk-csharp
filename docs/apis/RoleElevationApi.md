# Mudbase.SDK.Api.RoleElevationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**RoleElevationGetStatus**](RoleElevationApi.md#roleelevationgetstatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**RoleElevationRequest**](RoleElevationApi.md#roleelevationrequest) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**RoleElevationUploadDocuments**](RoleElevationApi.md#roleelevationuploaddocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |

<a id="roleelevationgetstatus"></a>
# **RoleElevationGetStatus**
> RoleElevationGetStatus200Response RoleElevationGetStatus (string projectId, string roleSlug = null)

Get role elevation status

Get status of pending role elevation requests for current user


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **roleSlug** | **string** | Optional filter by role slug. | [optional]  |

### Return type

[**RoleElevationGetStatus200Response**](RoleElevationGetStatus200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of role elevation requests |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="roleelevationrequest"></a>
# **RoleElevationRequest**
> RoleElevationRequest200Response RoleElevationRequest (string projectId, RoleElevationRequestRequest roleElevationRequestRequest)

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **roleElevationRequestRequest** | [**RoleElevationRequestRequest**](RoleElevationRequestRequest.md) | Role slug to request elevation to (e.g. vendor). |  |

### Return type

[**RoleElevationRequest200Response**](RoleElevationRequest200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role elevation request created or auto-approved |  -  |
| **400** | Invalid request or already has role |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Cannot request role with higher hierarchy |  -  |
| **404** | Role not found (exact backend message for role-elevation endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="roleelevationuploaddocuments"></a>
# **RoleElevationUploadDocuments**
> void RoleElevationUploadDocuments (string projectId, RoleElevationUploadDocumentsRequest roleElevationUploadDocumentsRequest)

Upload verification documents

Upload KYC/verification documents for role elevation


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **roleElevationUploadDocumentsRequest** | [**RoleElevationUploadDocumentsRequest**](RoleElevationUploadDocumentsRequest.md) | Role slug and array of document objects (type, url). |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Documents uploaded successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

