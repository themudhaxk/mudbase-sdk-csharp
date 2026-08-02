# Mudbase.SDK.Api.MultiRoleFeatureApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddCustomRole**](MultiRoleFeatureApi.md#addcustomrole) | **POST** /api/projects/{projectId}/multi-role/roles | Add custom role |
| [**ApplyRoleFeaturePreset**](MultiRoleFeatureApi.md#applyrolefeaturepreset) | **POST** /api/projects/{projectId}/multi-role/roles/{roleSlug}/apply-preset | Apply Admin / User / Viewer feature permission preset |
| [**GetAvailableRoles**](MultiRoleFeatureApi.md#getavailableroles) | **GET** /api/projects/{projectId}/multi-role/roles/available | Get available roles for signup |
| [**GetMultiRoleConfig**](MultiRoleFeatureApi.md#getmultiroleconfig) | **GET** /api/projects/{projectId}/multi-role | Get multi-role feature configuration |
| [**GetPermissionsMatrix**](MultiRoleFeatureApi.md#getpermissionsmatrix) | **GET** /api/projects/{projectId}/permissions-matrix | Get permissions matrix (collections + featurePermissions) |
| [**OauthSignupWithRole**](MultiRoleFeatureApi.md#oauthsignupwithrole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**RegisterWithRole**](MultiRoleFeatureApi.md#registerwithrole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |
| [**SimulateAppPermissions**](MultiRoleFeatureApi.md#simulateapppermissions) | **POST** /api/projects/{projectId}/multi-role/simulate-permissions | Simulate app-role feature permission for a path |
| [**ToggleRole**](MultiRoleFeatureApi.md#togglerole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/toggle | Toggle role on/off |
| [**UpdateCollectionPermissions**](MultiRoleFeatureApi.md#updatecollectionpermissions) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug}/collections/{collectionId}/permissions | Update collection permissions for a role |
| [**UpdateMultiRoleSettings**](MultiRoleFeatureApi.md#updatemultirolesettings) | **PATCH** /api/projects/{projectId}/multi-role/settings | Update multi-role feature settings |
| [**UpdateProjectRole**](MultiRoleFeatureApi.md#updateprojectrole) | **PATCH** /api/projects/{projectId}/multi-role/roles/{roleSlug} | Update role configuration |

<a id="addcustomrole"></a>
# **AddCustomRole**
> ApplyRoleFeaturePreset200Response AddCustomRole (string projectId, AddCustomRoleRequest addCustomRoleRequest)

Add custom role

Add a custom role to a project with specific permissions and signup endpoint. Optional **`featurePermissions`** must align with app JWT gates — see `components/schemas/AppRoleFeaturePermissions` and `services/appRoleFeatureMap.js`. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

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
    public class AddCustomRoleExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var addCustomRoleRequest = new AddCustomRoleRequest(); // AddCustomRoleRequest | 

            try
            {
                // Add custom role
                ApplyRoleFeaturePreset200Response result = apiInstance.AddCustomRole(projectId, addCustomRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.AddCustomRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AddCustomRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Add custom role
    ApiResponse<ApplyRoleFeaturePreset200Response> response = apiInstance.AddCustomRoleWithHttpInfo(projectId, addCustomRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.AddCustomRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **addCustomRoleRequest** | [**AddCustomRoleRequest**](AddCustomRoleRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Custom role added |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="applyrolefeaturepreset"></a>
# **ApplyRoleFeaturePreset**
> ApplyRoleFeaturePreset200Response ApplyRoleFeaturePreset (string projectId, string roleSlug, ApplyRoleFeaturePresetRequest applyRoleFeaturePresetRequest)

Apply Admin / User / Viewer feature permission preset

Sets `featurePermissions` on the role from a bundled preset (`admin`, `user`, `viewer`). Does not change collection CRUD or `dataScope`; use collection permission APIs for those. 

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
    public class ApplyRoleFeaturePresetExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var roleSlug = "roleSlug_example";  // string | 
            var applyRoleFeaturePresetRequest = new ApplyRoleFeaturePresetRequest(); // ApplyRoleFeaturePresetRequest | 

            try
            {
                // Apply Admin / User / Viewer feature permission preset
                ApplyRoleFeaturePreset200Response result = apiInstance.ApplyRoleFeaturePreset(projectId, roleSlug, applyRoleFeaturePresetRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.ApplyRoleFeaturePreset: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApplyRoleFeaturePresetWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Apply Admin / User / Viewer feature permission preset
    ApiResponse<ApplyRoleFeaturePreset200Response> response = apiInstance.ApplyRoleFeaturePresetWithHttpInfo(projectId, roleSlug, applyRoleFeaturePresetRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.ApplyRoleFeaturePresetWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string** |  |  |
| **applyRoleFeaturePresetRequest** | [**ApplyRoleFeaturePresetRequest**](ApplyRoleFeaturePresetRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Preset applied |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getavailableroles"></a>
# **GetAvailableRoles**
> GetAvailableRoles200Response GetAvailableRoles (string projectId)

Get available roles for signup

Get all available roles for user signup in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

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
    public class GetAvailableRolesExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 

            try
            {
                // Get available roles for signup
                GetAvailableRoles200Response result = apiInstance.GetAvailableRoles(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.GetAvailableRoles: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAvailableRolesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get available roles for signup
    ApiResponse<GetAvailableRoles200Response> response = apiInstance.GetAvailableRolesWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.GetAvailableRolesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetAvailableRoles200Response**](GetAvailableRoles200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available roles |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmultiroleconfig"></a>
# **GetMultiRoleConfig**
> GetMultiRoleConfig200Response GetMultiRoleConfig (string projectId)

Get multi-role feature configuration

Returns project app roles (default one editable `customer` starter until you add more) and settings

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
    public class GetMultiRoleConfigExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 

            try
            {
                // Get multi-role feature configuration
                GetMultiRoleConfig200Response result = apiInstance.GetMultiRoleConfig(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.GetMultiRoleConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMultiRoleConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get multi-role feature configuration
    ApiResponse<GetMultiRoleConfig200Response> response = apiInstance.GetMultiRoleConfigWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.GetMultiRoleConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetMultiRoleConfig200Response**](GetMultiRoleConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Multi-role configuration |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getpermissionsmatrix"></a>
# **GetPermissionsMatrix**
> GetPermissionsMatrix200Response GetPermissionsMatrix (string projectId)

Get permissions matrix (collections + featurePermissions)

Dashboard helper: per-collection permission rows (role actions, `dataScope`, conditions) and a per-role `featurePermissions` snapshot used by app-role feature gates (messaging, integrations, storage, etc.). 

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
    public class GetPermissionsMatrixExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 

            try
            {
                // Get permissions matrix (collections + featurePermissions)
                GetPermissionsMatrix200Response result = apiInstance.GetPermissionsMatrix(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.GetPermissionsMatrix: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetPermissionsMatrixWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get permissions matrix (collections + featurePermissions)
    ApiResponse<GetPermissionsMatrix200Response> response = apiInstance.GetPermissionsMatrixWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.GetPermissionsMatrixWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetPermissionsMatrix200Response**](GetPermissionsMatrix200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Matrix payload |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="oauthsignupwithrole"></a>
# **OauthSignupWithRole**
> void OauthSignupWithRole (string role, string provider, string projectId, string? redirectUrl = null)

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project's multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint. 

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
    public class OauthSignupWithRoleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var role = customer;  // string | Path segment must match the role's `signupEndpoint` (default `customer`; use each role's configured endpoint).
            var provider = google;  // string | 
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var redirectUrl = https://client.app/auth/callback;  // string? | The URL to redirect to after authentication (optional) 

            try
            {
                // OAuth signup with specific role
                apiInstance.OauthSignupWithRole(role, provider, projectId, redirectUrl);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.OauthSignupWithRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the OauthSignupWithRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // OAuth signup with specific role
    apiInstance.OauthSignupWithRoleWithHttpInfo(role, provider, projectId, redirectUrl);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.OauthSignupWithRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **role** | **string** | Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). |  |
| **provider** | **string** |  |  |
| **projectId** | **string** |  |  |
| **redirectUrl** | **string?** | The URL to redirect to after authentication | [optional]  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirects to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, role not found, or validation error |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="registerwithrole"></a>
# **RegisterWithRole**
> RegisterWithRole201Response RegisterWithRole (string role, RegisterWithRoleRequest registerWithRoleRequest)

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The path segment must match a role's `signupEndpoint` (default starter is `customer`; add more roles via multi-role API). No authentication required - this is a public signup endpoint. 

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
    public class RegisterWithRoleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var role = customer;  // string | Must match the role's `signupEndpoint` (default `customer`; other values for roles you add).
            var registerWithRoleRequest = new RegisterWithRoleRequest(); // RegisterWithRoleRequest | 

            try
            {
                // Register user with specific role (Local Auth)
                RegisterWithRole201Response result = apiInstance.RegisterWithRole(role, registerWithRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.RegisterWithRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RegisterWithRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Register user with specific role (Local Auth)
    ApiResponse<RegisterWithRole201Response> response = apiInstance.RegisterWithRoleWithHttpInfo(role, registerWithRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.RegisterWithRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **role** | **string** | Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). |  |
| **registerWithRoleRequest** | [**RegisterWithRoleRequest**](RegisterWithRoleRequest.md) |  |  |

### Return type

[**RegisterWithRole201Response**](RegisterWithRole201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Registration successful. Two response shapes depending on the project&#39;s &#x60;requireEmailVerification&#x60; setting - see &#x60;requireVerification&#x60; to distinguish them; &#x60;token&#x60;/&#x60;refreshToken&#x60;/&#x60;expiresIn&#x60; are only present when a session was issued immediately. |  -  |
| **400** | Validation failed, or a user with this email already exists for the project |  -  |
| **403** | Role requires approval, payment, or KYC before it can be self-assigned |  -  |
| **404** | Role not found or not enabled |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="simulateapppermissions"></a>
# **SimulateAppPermissions**
> SimulateAppPermissions200Response SimulateAppPermissions (string projectId, SimulateAppPermissionsRequest simulateAppPermissionsRequest)

Simulate app-role feature permission for a path

Dashboard-only. Given an app role slug and either an OpenAPI `operationId` **or** HTTP method + pathname, returns whether the role's `featurePermissions` would allow the operation for paths that have a feature gate. Unmapped paths or unknown operation IDs return `allowed: true` with reason `no_feature_gate_for_path` or `no_feature_gate_for_operation_id`. 

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
    public class SimulateAppPermissionsExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | 
            var simulateAppPermissionsRequest = new SimulateAppPermissionsRequest(); // SimulateAppPermissionsRequest | 

            try
            {
                // Simulate app-role feature permission for a path
                SimulateAppPermissions200Response result = apiInstance.SimulateAppPermissions(projectId, simulateAppPermissionsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.SimulateAppPermissions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SimulateAppPermissionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Simulate app-role feature permission for a path
    ApiResponse<SimulateAppPermissions200Response> response = apiInstance.SimulateAppPermissionsWithHttpInfo(projectId, simulateAppPermissionsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.SimulateAppPermissionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **simulateAppPermissionsRequest** | [**SimulateAppPermissionsRequest**](SimulateAppPermissionsRequest.md) |  |  |

### Return type

[**SimulateAppPermissions200Response**](SimulateAppPermissions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Simulation result |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="togglerole"></a>
# **ToggleRole**
> ApplyRoleFeaturePreset200Response ToggleRole (string projectId, string roleSlug, ToggleRoleRequest toggleRoleRequest)

Toggle role on/off

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
    public class ToggleRoleExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var roleSlug = customer;  // string | Role slug to toggle (e.g. starter `customer` or a role you added).
            var toggleRoleRequest = new ToggleRoleRequest(); // ToggleRoleRequest | 

            try
            {
                // Toggle role on/off
                ApplyRoleFeaturePreset200Response result = apiInstance.ToggleRole(projectId, roleSlug, toggleRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.ToggleRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ToggleRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Toggle role on/off
    ApiResponse<ApplyRoleFeaturePreset200Response> response = apiInstance.ToggleRoleWithHttpInfo(projectId, roleSlug, toggleRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.ToggleRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string** | Role slug to toggle (e.g. starter &#x60;customer&#x60; or a role you added). |  |
| **toggleRoleRequest** | [**ToggleRoleRequest**](ToggleRoleRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role toggled |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatecollectionpermissions"></a>
# **UpdateCollectionPermissions**
> ApplyRoleFeaturePreset200Response UpdateCollectionPermissions (string projectId, string roleSlug, string collectionId, UpdateCollectionPermissionsRequest updateCollectionPermissionsRequest)

Update collection permissions for a role

Update collection-specific permissions for a role in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

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
    public class UpdateCollectionPermissionsExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var roleSlug = customer;  // string | Role slug (e.g. starter `customer` or a role you added).
            var collectionId = 696ba6e4f4a9422ac4be4f74;  // string | 
            var updateCollectionPermissionsRequest = new UpdateCollectionPermissionsRequest(); // UpdateCollectionPermissionsRequest | 

            try
            {
                // Update collection permissions for a role
                ApplyRoleFeaturePreset200Response result = apiInstance.UpdateCollectionPermissions(projectId, roleSlug, collectionId, updateCollectionPermissionsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateCollectionPermissions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateCollectionPermissionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update collection permissions for a role
    ApiResponse<ApplyRoleFeaturePreset200Response> response = apiInstance.UpdateCollectionPermissionsWithHttpInfo(projectId, roleSlug, collectionId, updateCollectionPermissionsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateCollectionPermissionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string** | Role slug (e.g. starter &#x60;customer&#x60; or a role you added). |  |
| **collectionId** | **string** |  |  |
| **updateCollectionPermissionsRequest** | [**UpdateCollectionPermissionsRequest**](UpdateCollectionPermissionsRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Collection permissions updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatemultirolesettings"></a>
# **UpdateMultiRoleSettings**
> UpdateMultiRoleSettings200Response UpdateMultiRoleSettings (string projectId, UpdateMultiRoleSettingsRequest updateMultiRoleSettingsRequest)

Update multi-role feature settings

Update multi-role feature settings for a project: enable/disable the feature, set which app role is the default at signup, and tune `settings` (`allowMultipleRoles`, `requireRoleSelection`, `autoAssignDefault`). This endpoint does **not** edit role definitions or permissions — use `POST/PATCH .../multi-role/roles` for that (same shape as **Add custom role**). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 

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
    public class UpdateMultiRoleSettingsExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var updateMultiRoleSettingsRequest = new UpdateMultiRoleSettingsRequest(); // UpdateMultiRoleSettingsRequest | 

            try
            {
                // Update multi-role feature settings
                UpdateMultiRoleSettings200Response result = apiInstance.UpdateMultiRoleSettings(projectId, updateMultiRoleSettingsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateMultiRoleSettings: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateMultiRoleSettingsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update multi-role feature settings
    ApiResponse<UpdateMultiRoleSettings200Response> response = apiInstance.UpdateMultiRoleSettingsWithHttpInfo(projectId, updateMultiRoleSettingsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateMultiRoleSettingsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **updateMultiRoleSettingsRequest** | [**UpdateMultiRoleSettingsRequest**](UpdateMultiRoleSettingsRequest.md) |  |  |

### Return type

[**UpdateMultiRoleSettings200Response**](UpdateMultiRoleSettings200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Settings updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateprojectrole"></a>
# **UpdateProjectRole**
> ApplyRoleFeaturePreset200Response UpdateProjectRole (string projectId, string roleSlug, UpdateProjectRoleRequest updateProjectRoleRequest)

Update role configuration

Partial update of an app role. **`featurePermissions`** keys must match the app-role gate map (`services/appRoleFeatureMap.js`); schema: `components/schemas/AppRoleFeaturePermissions`. 

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
    public class UpdateProjectRoleExample
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
            var apiInstance = new MultiRoleFeatureApi(httpClient, config, httpClientHandler);
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var roleSlug = customer;  // string | Role slug to update (e.g. starter `customer` or a role you added).
            var updateProjectRoleRequest = new UpdateProjectRoleRequest(); // UpdateProjectRoleRequest | Same fields as **Add custom role** — send only fields you want to change. `defaultPermissions` / `collectionPermissions` are normalized the same way as on create. **`featurePermissions`:** `components/schemas/AppRoleFeaturePermissions` (aligned with `services/appRoleFeatureMap.js`). 

            try
            {
                // Update role configuration
                ApplyRoleFeaturePreset200Response result = apiInstance.UpdateProjectRole(projectId, roleSlug, updateProjectRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateProjectRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateProjectRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update role configuration
    ApiResponse<ApplyRoleFeaturePreset200Response> response = apiInstance.UpdateProjectRoleWithHttpInfo(projectId, roleSlug, updateProjectRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MultiRoleFeatureApi.UpdateProjectRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **roleSlug** | **string** | Role slug to update (e.g. starter &#x60;customer&#x60; or a role you added). |  |
| **updateProjectRoleRequest** | [**UpdateProjectRoleRequest**](UpdateProjectRoleRequest.md) | Same fields as **Add custom role** — send only fields you want to change. &#x60;defaultPermissions&#x60; / &#x60;collectionPermissions&#x60; are normalized the same way as on create. **&#x60;featurePermissions&#x60;:** &#x60;components/schemas/AppRoleFeaturePermissions&#x60; (aligned with &#x60;services/appRoleFeatureMap.js&#x60;).  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

