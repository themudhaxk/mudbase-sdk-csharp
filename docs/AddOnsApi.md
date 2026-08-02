# Mudbase.SDK.Api.AddOnsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiAddonsGet**](AddOnsApi.md#apiaddonsget) | **GET** /api/addons | List the add-on catalog |
| [**ApiProjectsProjectIdAddonsAddonInvokePost**](AddOnsApi.md#apiprojectsprojectidaddonsaddoninvokepost) | **POST** /api/projects/{projectId}/addons/{addon}/invoke | Invoke an add-on for a project |
| [**ApiProjectsProjectIdAddonsJobsIdGet**](AddOnsApi.md#apiprojectsprojectidaddonsjobsidget) | **GET** /api/projects/{projectId}/addons/jobs/{id} | Get an add-on job status |

<a id="apiaddonsget"></a>
# **ApiAddonsGet**
> ApiAddonsGet200Response ApiAddonsGet ()

List the add-on catalog

Returns the available add-ons (key, metadata, pricing) the caller can invoke.

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
    public class ApiAddonsGetExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new AddOnsApi(httpClient, config, httpClientHandler);

            try
            {
                // List the add-on catalog
                ApiAddonsGet200Response result = apiInstance.ApiAddonsGet();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AddOnsApi.ApiAddonsGet: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApiAddonsGetWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List the add-on catalog
    ApiResponse<ApiAddonsGet200Response> response = apiInstance.ApiAddonsGetWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AddOnsApi.ApiAddonsGetWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiAddonsGet200Response**](ApiAddonsGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on catalog |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="apiprojectsprojectidaddonsaddoninvokepost"></a>
# **ApiProjectsProjectIdAddonsAddonInvokePost**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response ApiProjectsProjectIdAddonsAddonInvokePost (string projectId, string addon, Object? body = null)

Invoke an add-on for a project

Runs the named add-on against the project. Returns the job synchronously (200) when it completes immediately, or 202 with a pending job when processing continues in the background.

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
    public class ApiProjectsProjectIdAddonsAddonInvokePostExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("X-API-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-API-Key", "Bearer");
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new AddOnsApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var addon = "addon_example";  // string | Add-on key from the catalog.
            var body = null;  // Object? |  (optional) 

            try
            {
                // Invoke an add-on for a project
                ApiProjectsProjectIdAddonsAddonInvokePost200Response result = apiInstance.ApiProjectsProjectIdAddonsAddonInvokePost(projectId, addon, body);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AddOnsApi.ApiProjectsProjectIdAddonsAddonInvokePost: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApiProjectsProjectIdAddonsAddonInvokePostWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Invoke an add-on for a project
    ApiResponse<ApiProjectsProjectIdAddonsAddonInvokePost200Response> response = apiInstance.ApiProjectsProjectIdAddonsAddonInvokePostWithHttpInfo(projectId, addon, body);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AddOnsApi.ApiProjectsProjectIdAddonsAddonInvokePostWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **addon** | **string** | Add-on key from the catalog. |  |
| **body** | **Object?** |  | [optional]  |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on job completed |  -  |
| **202** | Add-on job accepted and processing |  -  |
| **400** | Invalid add-on key or input |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="apiprojectsprojectidaddonsjobsidget"></a>
# **ApiProjectsProjectIdAddonsJobsIdGet**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response ApiProjectsProjectIdAddonsJobsIdGet (string projectId, string id)

Get an add-on job status

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
    public class ApiProjectsProjectIdAddonsJobsIdGetExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("X-API-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-API-Key", "Bearer");
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new AddOnsApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var id = "id_example";  // string | Add-on job id.

            try
            {
                // Get an add-on job status
                ApiProjectsProjectIdAddonsAddonInvokePost200Response result = apiInstance.ApiProjectsProjectIdAddonsJobsIdGet(projectId, id);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling AddOnsApi.ApiProjectsProjectIdAddonsJobsIdGet: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApiProjectsProjectIdAddonsJobsIdGetWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get an add-on job status
    ApiResponse<ApiProjectsProjectIdAddonsAddonInvokePost200Response> response = apiInstance.ApiProjectsProjectIdAddonsJobsIdGetWithHttpInfo(projectId, id);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling AddOnsApi.ApiProjectsProjectIdAddonsJobsIdGetWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **id** | **string** | Add-on job id. |  |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The add-on job |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |
| **404** | Add-on job not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

