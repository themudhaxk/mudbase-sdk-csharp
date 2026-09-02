# Mudbase.SDK.Api.ProjectsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ConfigureOAuthProvider**](ProjectsApi.md#configureoauthprovider) | **POST** /api/auth/oauth/projects/{projectId}/providers/{provider} | Configure OAuth provider for a project |
| [**CreateProject**](ProjectsApi.md#createproject) | **POST** /api/projects/{orgId}/projects | Create new project |
| [**DeleteProject**](ProjectsApi.md#deleteproject) | **DELETE** /api/projects/{orgId}/projects/{id} | Delete project |
| [**GetOAuthProviderConfig**](ProjectsApi.md#getoauthproviderconfig) | **GET** /api/auth/oauth/projects/{projectId}/providers/{provider} | Get OAuth provider configuration |
| [**GetProject**](ProjectsApi.md#getproject) | **GET** /api/projects/{orgId}/projects/{id} | Get single project |
| [**GetProjectCaptchaConfig**](ProjectsApi.md#getprojectcaptchaconfig) | **GET** /api/projects/{orgId}/projects/{id}/auth/captcha | Get project CAPTCHA configuration |
| [**GetProjectDashboardOverview**](ProjectsApi.md#getprojectdashboardoverview) | **GET** /api/projects/{projectId}/dashboard/overview | Project dashboard overview |
| [**GetProjectOAuthProviders**](ProjectsApi.md#getprojectoauthproviders) | **GET** /api/auth/oauth/projects/{projectId}/providers | Get configured OAuth providers for a project |
| [**GetProjectUsage**](ProjectsApi.md#getprojectusage) | **GET** /api/projects/{orgId}/projects/{id}/usage | Get project usage statistics |
| [**ListProjects**](ProjectsApi.md#listprojects) | **GET** /api/projects/{orgId}/projects | List all projects |
| [**UpdateOAuthProviderConfig**](ProjectsApi.md#updateoauthproviderconfig) | **PATCH** /api/auth/oauth/projects/{projectId}/providers/{provider} | Update OAuth provider configuration |
| [**UpdateProject**](ProjectsApi.md#updateproject) | **PATCH** /api/projects/{orgId}/projects/{id} | Update project |
| [**UploadProjectLogo**](ProjectsApi.md#uploadprojectlogo) | **POST** /api/projects/{id}/logo | Upload project logo (by project ID) |
| [**UploadProjectLogoByOrg**](ProjectsApi.md#uploadprojectlogobyorg) | **POST** /api/projects/{orgId}/projects/{id}/logo | Upload project logo (by org and project ID) |

<a id="configureoauthprovider"></a>
# **ConfigureOAuthProvider**
> ConfigureOAuthProvider200Response ConfigureOAuthProvider (string projectId, string provider, ConfigureOAuthProviderRequest configureOAuthProviderRequest)

Configure OAuth provider for a project

Creates or updates the configuration for an OAuth provider for the specified project

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
    public class ConfigureOAuthProviderExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var provider = google;  // string | 
            var configureOAuthProviderRequest = new ConfigureOAuthProviderRequest(); // ConfigureOAuthProviderRequest | 

            try
            {
                // Configure OAuth provider for a project
                ConfigureOAuthProvider200Response result = apiInstance.ConfigureOAuthProvider(projectId, provider, configureOAuthProviderRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.ConfigureOAuthProvider: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ConfigureOAuthProviderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Configure OAuth provider for a project
    ApiResponse<ConfigureOAuthProvider200Response> response = apiInstance.ConfigureOAuthProviderWithHttpInfo(projectId, provider, configureOAuthProviderRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.ConfigureOAuthProviderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **provider** | **string** |  |  |
| **configureOAuthProviderRequest** | [**ConfigureOAuthProviderRequest**](ConfigureOAuthProviderRequest.md) |  |  |

### Return type

[**ConfigureOAuthProvider200Response**](ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configured successfully |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createproject"></a>
# **CreateProject**
> CreateProject201Response CreateProject (string orgId, CreateProjectRequest createProjectRequest)

Create new project

Create a new project in an organization. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class CreateProjectExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var createProjectRequest = new CreateProjectRequest(); // CreateProjectRequest | 

            try
            {
                // Create new project
                CreateProject201Response result = apiInstance.CreateProject(orgId, createProjectRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.CreateProject: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateProjectWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create new project
    ApiResponse<CreateProject201Response> response = apiInstance.CreateProjectWithHttpInfo(orgId, createProjectRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.CreateProjectWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **createProjectRequest** | [**CreateProjectRequest**](CreateProjectRequest.md) |  |  |

### Return type

[**CreateProject201Response**](CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Project created |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteproject"></a>
# **DeleteProject**
> MessageResponse DeleteProject (string orgId, string id)

Delete project

Delete a project permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class DeleteProjectExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID

            try
            {
                // Delete project
                MessageResponse result = apiInstance.DeleteProject(orgId, id);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.DeleteProject: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteProjectWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete project
    ApiResponse<MessageResponse> response = apiInstance.DeleteProjectWithHttpInfo(orgId, id);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.DeleteProjectWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project deleted |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getoauthproviderconfig"></a>
# **GetOAuthProviderConfig**
> GetOAuthProviderConfig200Response GetOAuthProviderConfig (string projectId, string provider)

Get OAuth provider configuration

Returns the configuration for a specific OAuth provider for the project (without sensitive data)

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
    public class GetOAuthProviderConfigExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var provider = google;  // string | 

            try
            {
                // Get OAuth provider configuration
                GetOAuthProviderConfig200Response result = apiInstance.GetOAuthProviderConfig(projectId, provider);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetOAuthProviderConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOAuthProviderConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get OAuth provider configuration
    ApiResponse<GetOAuthProviderConfig200Response> response = apiInstance.GetOAuthProviderConfigWithHttpInfo(projectId, provider);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetOAuthProviderConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **provider** | **string** |  |  |

### Return type

[**GetOAuthProviderConfig200Response**](GetOAuthProviderConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configuration |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getproject"></a>
# **GetProject**
> Project GetProject (string orgId, string id)

Get single project

Get project details by ID. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

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
    public class GetProjectExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID

            try
            {
                // Get single project
                Project result = apiInstance.GetProject(orgId, id);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetProject: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get single project
    ApiResponse<Project> response = apiInstance.GetProjectWithHttpInfo(orgId, id);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetProjectWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |

### Return type

[**Project**](Project.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project details |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprojectcaptchaconfig"></a>
# **GetProjectCaptchaConfig**
> GetProjectCaptchaConfig200Response GetProjectCaptchaConfig (string orgId, string id)

Get project CAPTCHA configuration

Get CAPTCHA configuration for a project. This is a public endpoint that returns the site key  and settings needed for frontend integration. Secret key is never returned. 

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
    public class GetProjectCaptchaConfigExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID

            try
            {
                // Get project CAPTCHA configuration
                GetProjectCaptchaConfig200Response result = apiInstance.GetProjectCaptchaConfig(orgId, id);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetProjectCaptchaConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectCaptchaConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get project CAPTCHA configuration
    ApiResponse<GetProjectCaptchaConfig200Response> response = apiInstance.GetProjectCaptchaConfigWithHttpInfo(orgId, id);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetProjectCaptchaConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |

### Return type

[**GetProjectCaptchaConfig200Response**](GetProjectCaptchaConfig200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | CAPTCHA configuration |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprojectdashboardoverview"></a>
# **GetProjectDashboardOverview**
> ProjectDashboardOverviewResponse GetProjectDashboardOverview (string projectId)

Project dashboard overview

Single response for the project overview UI: project info, request counts and day-over-day % change, active users (distinct JWT users with project activity; realtime socket count when available), **Uptime** (30d headline) is organization-wide when enough HTTP samples exist, else DB heartbeat probes. **Average latency** (today / 7d) is **per project** and counts only routes documented in `openapi-docs.yaml` for customer/project API (excludes auth, `/api/users`, `/api/orgs`, role-elevation, and multi-role admin routes). Request volume and active users remain per-project. 14-day API call volume and recent audit activity are per-project. See docs/dashboard-overview-api.md. 

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
    public class GetProjectDashboardOverviewExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("X-API-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-API-Key", "Bearer");
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 

            try
            {
                // Project dashboard overview
                ProjectDashboardOverviewResponse result = apiInstance.GetProjectDashboardOverview(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetProjectDashboardOverview: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectDashboardOverviewWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Project dashboard overview
    ApiResponse<ProjectDashboardOverviewResponse> response = apiInstance.GetProjectDashboardOverviewWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetProjectDashboardOverviewWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**ProjectDashboardOverviewResponse**](ProjectDashboardOverviewResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Dashboard overview |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprojectoauthproviders"></a>
# **GetProjectOAuthProviders**
> GetProjectOAuthProviders200Response GetProjectOAuthProviders (string projectId)

Get configured OAuth providers for a project

Returns a list of OAuth providers that are configured and enabled for the specified project

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
    public class GetProjectOAuthProvidersExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 

            try
            {
                // Get configured OAuth providers for a project
                GetProjectOAuthProviders200Response result = apiInstance.GetProjectOAuthProviders(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetProjectOAuthProviders: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectOAuthProvidersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get configured OAuth providers for a project
    ApiResponse<GetProjectOAuthProviders200Response> response = apiInstance.GetProjectOAuthProvidersWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetProjectOAuthProvidersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetProjectOAuthProviders200Response**](GetProjectOAuthProviders200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of configured OAuth providers |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprojectusage"></a>
# **GetProjectUsage**
> ProjectUsageResponse GetProjectUsage (string orgId, string id)

Get project usage statistics

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
    public class GetProjectUsageExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID

            try
            {
                // Get project usage statistics
                ProjectUsageResponse result = apiInstance.GetProjectUsage(orgId, id);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.GetProjectUsage: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectUsageWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get project usage statistics
    ApiResponse<ProjectUsageResponse> response = apiInstance.GetProjectUsageWithHttpInfo(orgId, id);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.GetProjectUsageWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |

### Return type

[**ProjectUsageResponse**](ProjectUsageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project usage statistics |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprojects"></a>
# **ListProjects**
> ListProjects200Response ListProjects (string orgId)

List all projects

List all projects in an organization. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class ListProjectsExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID

            try
            {
                // List all projects
                ListProjects200Response result = apiInstance.ListProjects(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.ListProjects: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListProjectsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List all projects
    ApiResponse<ListProjects200Response> response = apiInstance.ListProjectsWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.ListProjectsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |

### Return type

[**ListProjects200Response**](ListProjects200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Projects list |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateoauthproviderconfig"></a>
# **UpdateOAuthProviderConfig**
> ConfigureOAuthProvider200Response UpdateOAuthProviderConfig (string projectId, string provider, UpdateOAuthProviderConfigRequest updateOAuthProviderConfigRequest)

Update OAuth provider configuration

Updates the configuration for an OAuth provider for the specified project

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
    public class UpdateOAuthProviderConfigExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var provider = google;  // string | 
            var updateOAuthProviderConfigRequest = new UpdateOAuthProviderConfigRequest(); // UpdateOAuthProviderConfigRequest | 

            try
            {
                // Update OAuth provider configuration
                ConfigureOAuthProvider200Response result = apiInstance.UpdateOAuthProviderConfig(projectId, provider, updateOAuthProviderConfigRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.UpdateOAuthProviderConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateOAuthProviderConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update OAuth provider configuration
    ApiResponse<ConfigureOAuthProvider200Response> response = apiInstance.UpdateOAuthProviderConfigWithHttpInfo(projectId, provider, updateOAuthProviderConfigRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.UpdateOAuthProviderConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **provider** | **string** |  |  |
| **updateOAuthProviderConfigRequest** | [**UpdateOAuthProviderConfigRequest**](UpdateOAuthProviderConfigRequest.md) |  |  |

### Return type

[**ConfigureOAuthProvider200Response**](ConfigureOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OAuth provider configuration updated successfully |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateproject"></a>
# **UpdateProject**
> CreateProject201Response UpdateProject (string orgId, string id, UpdateProjectRequest updateProjectRequest)

Update project

Update project configuration (name, description, settings). **Settings toggles:** **requireEmailVerification** (default true) — when on, new email signups do not get a token until they verify; login is blocked until verified. **requirePhoneVerification** (default false) — when on, phone/OTP users must verify before token. **defaultUserAccountStatus** — **active** (default) or **pending**; when pending, new users must be approved by org owner/admin before they can perform data/storage operations. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class UpdateProjectExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID
            var updateProjectRequest = new UpdateProjectRequest(); // UpdateProjectRequest | 

            try
            {
                // Update project
                CreateProject201Response result = apiInstance.UpdateProject(orgId, id, updateProjectRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.UpdateProject: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateProjectWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update project
    ApiResponse<CreateProject201Response> response = apiInstance.UpdateProjectWithHttpInfo(orgId, id, updateProjectRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.UpdateProjectWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |
| **updateProjectRequest** | [**UpdateProjectRequest**](UpdateProjectRequest.md) |  |  |

### Return type

[**CreateProject201Response**](CreateProject201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadprojectlogo"></a>
# **UploadProjectLogo**
> UploadProjectLogo200Response UploadProjectLogo (string id, FileParameter logo)

Upload project logo (by project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field and used in project-related emails and UI. Project is resolved from the authenticated user's org. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. 

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
    public class UploadProjectLogoExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure API key authorization: ApiKeyAuth
            config.AddApiKey("X-API-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-API-Key", "Bearer");
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var id = "id_example";  // string | Project ID
            var logo = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // FileParameter | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)

            try
            {
                // Upload project logo (by project ID)
                UploadProjectLogo200Response result = apiInstance.UploadProjectLogo(id, logo);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.UploadProjectLogo: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadProjectLogoWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload project logo (by project ID)
    ApiResponse<UploadProjectLogo200Response> response = apiInstance.UploadProjectLogoWithHttpInfo(id, logo);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.UploadProjectLogoWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** | Project ID |  |
| **logo** | **FileParameter****FileParameter** | Logo image (PNG, JPEG, GIF, or WebP; max 2MB) |  |

### Return type

[**UploadProjectLogo200Response**](UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logo uploaded and project logoUrl updated |  -  |
| **400** | No file, invalid type, or size exceeded |  -  |
| **404** | Project not found |  -  |
| **503** | Object storage not configured |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="uploadprojectlogobyorg"></a>
# **UploadProjectLogoByOrg**
> UploadProjectLogo200Response UploadProjectLogoByOrg (string orgId, string id, FileParameter logo)

Upload project logo (by org and project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. Requires project update permission and membership in the organization. 

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
    public class UploadProjectLogoByOrgExample
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
            var apiInstance = new ProjectsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | Organization ID
            var id = "id_example";  // string | Project ID
            var logo = new System.IO.MemoryStream(System.IO.File.ReadAllBytes("/path/to/file.txt"));  // FileParameter | Logo image (PNG, JPEG, GIF, or WebP; max 2MB)

            try
            {
                // Upload project logo (by org and project ID)
                UploadProjectLogo200Response result = apiInstance.UploadProjectLogoByOrg(orgId, id, logo);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProjectsApi.UploadProjectLogoByOrg: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UploadProjectLogoByOrgWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Upload project logo (by org and project ID)
    ApiResponse<UploadProjectLogo200Response> response = apiInstance.UploadProjectLogoByOrgWithHttpInfo(orgId, id, logo);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProjectsApi.UploadProjectLogoByOrgWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |
| **logo** | **FileParameter****FileParameter** | Logo image (PNG, JPEG, GIF, or WebP; max 2MB) |  |

### Return type

[**UploadProjectLogo200Response**](UploadProjectLogo200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logo uploaded and project logoUrl updated |  -  |
| **400** | No file, invalid type, or size exceeded |  -  |
| **404** | Project or organization not found |  -  |
| **503** | Object storage not configured |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

