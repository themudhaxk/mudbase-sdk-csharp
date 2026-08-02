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

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class ApproveRoleElevationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new RoleElevationApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var requestId = "requestId_example";  // string | 
            var approveRoleElevationRequest = new ApproveRoleElevationRequest(); // ApproveRoleElevationRequest | 

            try
            {
                // Approve/reject role elevation request (admin only)
                ApproveRoleElevation200Response result = apiInstance.ApproveRoleElevation(orgId, requestId, approveRoleElevationRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RoleElevationApi.ApproveRoleElevation: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApproveRoleElevationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Approve/reject role elevation request (admin only)
    ApiResponse<ApproveRoleElevation200Response> response = apiInstance.ApproveRoleElevationWithHttpInfo(orgId, requestId, approveRoleElevationRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RoleElevationApi.ApproveRoleElevationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpendingroleelevationrequests"></a>
# **GetPendingRoleElevationRequests**
> GetPendingRoleElevationRequests200Response GetPendingRoleElevationRequests (string orgId, string? status = null, int? page = null, int? limit = null)

Get pending role elevation requests (admin only)

Get all pending role elevation requests requiring admin approval

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetPendingRoleElevationRequestsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new RoleElevationApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var status = "pending";  // string? |  (optional)  (default to pending)
            var page = 1;  // int? |  (optional)  (default to 1)
            var limit = 50;  // int? |  (optional)  (default to 50)

            try
            {
                // Get pending role elevation requests (admin only)
                GetPendingRoleElevationRequests200Response result = apiInstance.GetPendingRoleElevationRequests(orgId, status, page, limit);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RoleElevationApi.GetPendingRoleElevationRequests: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPendingRoleElevationRequestsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get pending role elevation requests (admin only)
    ApiResponse<GetPendingRoleElevationRequests200Response> response = apiInstance.GetPendingRoleElevationRequestsWithHttpInfo(orgId, status, page, limit);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RoleElevationApi.GetPendingRoleElevationRequestsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **status** | **string?** |  | [optional] [default to pending] |
| **page** | **int?** |  | [optional] [default to 1] |
| **limit** | **int?** |  | [optional] [default to 50] |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getroleelevationstatus"></a>
# **GetRoleElevationStatus**
> GetRoleElevationStatus200Response GetRoleElevationStatus (string projectId, string? roleSlug = null)

Get role elevation status

Get status of pending role elevation requests for current user

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetRoleElevationStatusExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new RoleElevationApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var roleSlug = "roleSlug_example";  // string? |  (optional) 

            try
            {
                // Get role elevation status
                GetRoleElevationStatus200Response result = apiInstance.GetRoleElevationStatus(projectId, roleSlug);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RoleElevationApi.GetRoleElevationStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetRoleElevationStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get role elevation status
    ApiResponse<GetRoleElevationStatus200Response> response = apiInstance.GetRoleElevationStatusWithHttpInfo(projectId, roleSlug);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RoleElevationApi.GetRoleElevationStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string?** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="requestroleelevation"></a>
# **RequestRoleElevation**
> RequestRoleElevation200Response RequestRoleElevation (string projectId, RequestRoleElevationRequest requestRoleElevationRequest)

Request role elevation

User requests to upgrade to a specific role. May require payment, KYC, or admin approval based on role configuration.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class RequestRoleElevationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new RoleElevationApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var requestRoleElevationRequest = new RequestRoleElevationRequest(); // RequestRoleElevationRequest | 

            try
            {
                // Request role elevation
                RequestRoleElevation200Response result = apiInstance.RequestRoleElevation(projectId, requestRoleElevationRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RoleElevationApi.RequestRoleElevation: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RequestRoleElevationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Request role elevation
    ApiResponse<RequestRoleElevation200Response> response = apiInstance.RequestRoleElevationWithHttpInfo(projectId, requestRoleElevationRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RoleElevationApi.RequestRoleElevationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadverificationdocuments"></a>
# **UploadVerificationDocuments**
> void UploadVerificationDocuments (string projectId, UploadVerificationDocumentsRequest uploadVerificationDocumentsRequest)

Upload verification documents

Upload KYC/verification documents for role elevation

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class UploadVerificationDocumentsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new RoleElevationApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var uploadVerificationDocumentsRequest = new UploadVerificationDocumentsRequest(); // UploadVerificationDocumentsRequest | 

            try
            {
                // Upload verification documents
                apiInstance.UploadVerificationDocuments(projectId, uploadVerificationDocumentsRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling RoleElevationApi.UploadVerificationDocuments: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadVerificationDocumentsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload verification documents
    apiInstance.UploadVerificationDocumentsWithHttpInfo(projectId, uploadVerificationDocumentsRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling RoleElevationApi.UploadVerificationDocumentsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

