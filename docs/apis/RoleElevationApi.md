# Mudbase.SDK.Api.RoleElevationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApproveRoleElevation**](RoleElevationApi.md#approveroleelevation) | **POST** /api/orgs/{orgId}/role-elevation/{requestId}/approve | Approve/reject role elevation request (admin only) |
| [**GetPendingRoleElevationRequests**](RoleElevationApi.md#getpendingroleelevationrequests) | **GET** /api/orgs/{orgId}/role-elevation/pending | Get pending role elevation requests (admin only) |
| [**GetRoleElevationStatus**](RoleElevationApi.md#getroleelevationstatus) | **GET** /api/projects/{projectId}/role-elevation/status | Get role elevation status |
| [**RequestRoleElevation**](RoleElevationApi.md#requestroleelevation) | **POST** /api/projects/{projectId}/role-elevation/request | Request role elevation |
| [**UploadVerificationDocuments**](RoleElevationApi.md#uploadverificationdocuments) | **POST** /api/projects/{projectId}/role-elevation/documents | Upload verification documents |

<a id="approveroleelevation"></a>
# **ApproveRoleElevation**
> ApproveRoleElevation200Response ApproveRoleElevation (string orgId, string requestId, ApproveRoleElevationRequest approveRoleElevationRequest)

Approve/reject role elevation request (admin only)

Admin approves or rejects a role elevation request


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **requestId** | **string** |  |  |
| **approveRoleElevationRequest** | [**ApproveRoleElevationRequest**](ApproveRoleElevationRequest.md) |  |  |

### Return type

[**ApproveRoleElevation200Response**](ApproveRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Request approved/rejected |  -  |
| **400** | Requirements not met |  -  |
| **403** | Insufficient permissions |  -  |
| **404** | Request not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getpendingroleelevationrequests"></a>
# **GetPendingRoleElevationRequests**
> GetPendingRoleElevationRequests200Response GetPendingRoleElevationRequests (string orgId, string status = null, int page = null, int limit = null)

Get pending role elevation requests (admin only)

Get all pending role elevation requests requiring admin approval


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **status** | **string** |  | [optional] [default to pending] |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 50] |

### Return type

[**GetPendingRoleElevationRequests200Response**](GetPendingRoleElevationRequests200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of pending requests |  -  |
| **403** | Insufficient permissions |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getroleelevationstatus"></a>
# **GetRoleElevationStatus**
> GetRoleElevationStatus200Response GetRoleElevationStatus (string projectId, string roleSlug = null)

Get role elevation status

Get status of pending role elevation requests for current user


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string** |  | [optional]  |

### Return type

[**GetRoleElevationStatus200Response**](GetRoleElevationStatus200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of role elevation requests |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="requestroleelevation"></a>
# **RequestRoleElevation**
> RequestRoleElevation200Response RequestRoleElevation (string projectId, RequestRoleElevationRequest requestRoleElevationRequest)

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **requestRoleElevationRequest** | [**RequestRoleElevationRequest**](RequestRoleElevationRequest.md) |  |  |

### Return type

[**RequestRoleElevation200Response**](RequestRoleElevation200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role elevation request created or auto-approved |  -  |
| **400** | Invalid request or already has role |  -  |
| **403** | Cannot request role with higher hierarchy |  -  |
| **404** | Role not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="uploadverificationdocuments"></a>
# **UploadVerificationDocuments**
> void UploadVerificationDocuments (string projectId, UploadVerificationDocumentsRequest uploadVerificationDocumentsRequest)

Upload verification documents

Upload KYC/verification documents for role elevation


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **uploadVerificationDocumentsRequest** | [**UploadVerificationDocumentsRequest**](UploadVerificationDocumentsRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Documents uploaded successfully |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

