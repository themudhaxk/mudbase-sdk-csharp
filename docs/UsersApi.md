# Mudbase.SDK.Api.UsersApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiMeBootstrapGet**](UsersApi.md#apimebootstrapget) | **GET** /api/me/bootstrap | Dashboard bootstrap (session + orgs + default org + projects) |
| [**ChangePassword**](UsersApi.md#changepassword) | **PATCH** /api/users/password | Change password |
| [**Disable2FA**](UsersApi.md#disable2fa) | **POST** /api/users/2fa/disable | Disable 2FA |
| [**EraseUserData**](UsersApi.md#eraseuserdata) | **POST** /api/users/me/erase | Delete user data (GDPR Article 17) |
| [**ExportUserData**](UsersApi.md#exportuserdata) | **GET** /api/users/me/export | Export user data (GDPR Article 15) |
| [**GetCurrentUser**](UsersApi.md#getcurrentuser) | **GET** /api/users/me | Get current user profile |
| [**LinkOAuthProvider**](UsersApi.md#linkoauthprovider) | **GET** /api/users/me/oauth-providers/link/{provider} | Link OAuth provider to account |
| [**ListOAuthProviders**](UsersApi.md#listoauthproviders) | **GET** /api/users/me/oauth-providers | List linked OAuth providers |
| [**ResendVerificationEmail**](UsersApi.md#resendverificationemail) | **POST** /api/users/resend-verification | Resend verification email |
| [**Setup2FA**](UsersApi.md#setup2fa) | **POST** /api/users/2fa/setup | Setup 2FA |
| [**UnlinkOAuthProvider**](UsersApi.md#unlinkoauthprovider) | **DELETE** /api/users/me/oauth-providers/{provider} | Unlink OAuth provider |
| [**UpdateUserProfile**](UsersApi.md#updateuserprofile) | **PATCH** /api/users/update | Update user profile |
| [**Verify2FA**](UsersApi.md#verify2fa) | **POST** /api/users/2fa/verify | Verify and enable 2FA |
| [**VerifyEmail**](UsersApi.md#verifyemail) | **POST** /api/users/verify-email | Verify email address (organization and project) |

<a id="apimebootstrapget"></a>
# **ApiMeBootstrapGet**
> ApiMeBootstrapGet200Response ApiMeBootstrapGet ()

Dashboard bootstrap (session + orgs + default org + projects)

Consolidated dashboard warmup in a single round-trip. Returns the session user, the user's organizations, the resolved default organization, and that org's projects. Shapes match GET /api/auth/session, GET /api/orgs and GET /api/projects.

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
    public class ApiMeBootstrapGetExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // Dashboard bootstrap (session + orgs + default org + projects)
                ApiMeBootstrapGet200Response result = apiInstance.ApiMeBootstrapGet();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.ApiMeBootstrapGet: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ApiMeBootstrapGetWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Dashboard bootstrap (session + orgs + default org + projects)
    ApiResponse<ApiMeBootstrapGet200Response> response = apiInstance.ApiMeBootstrapGetWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.ApiMeBootstrapGetWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiMeBootstrapGet200Response**](ApiMeBootstrapGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bootstrap payload |  -  |
| **401** | Authentication required |  -  |
| **500** | Failed to load bootstrap data |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="changepassword"></a>
# **ChangePassword**
> MessageResponse ChangePassword (ChangePasswordRequest changePasswordRequest)

Change password

Change the current user's password. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 

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
    public class ChangePasswordExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var changePasswordRequest = new ChangePasswordRequest(); // ChangePasswordRequest | 

            try
            {
                // Change password
                MessageResponse result = apiInstance.ChangePassword(changePasswordRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.ChangePassword: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ChangePasswordWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Change password
    ApiResponse<MessageResponse> response = apiInstance.ChangePasswordWithHttpInfo(changePasswordRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.ChangePasswordWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **changePasswordRequest** | [**ChangePasswordRequest**](ChangePasswordRequest.md) |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password changed |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="disable2fa"></a>
# **Disable2FA**
> MessageResponse Disable2FA (Disable2FARequest disable2FARequest)

Disable 2FA

Disable two-factor authentication for the current user. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

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
    public class Disable2FAExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var disable2FARequest = new Disable2FARequest(); // Disable2FARequest | 

            try
            {
                // Disable 2FA
                MessageResponse result = apiInstance.Disable2FA(disable2FARequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.Disable2FA: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the Disable2FAWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Disable 2FA
    ApiResponse<MessageResponse> response = apiInstance.Disable2FAWithHttpInfo(disable2FARequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.Disable2FAWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **disable2FARequest** | [**Disable2FARequest**](Disable2FARequest.md) |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA disabled |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="eraseuserdata"></a>
# **EraseUserData**
> EraseUserData200Response EraseUserData (EraseUserDataRequest eraseUserDataRequest)

Delete user data (GDPR Article 17)

Request account erasure (right to be forgotten). Anonymizes PII, revokes all sessions and API keys, and disables the account immediately (not a grace period - the effect is immediate and irreversible). Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint.  Requires re-proving your current password (skipped only for OAuth-only accounts with no password set) and, if 2FA is enabled, a fresh TOTP code - the same step-up re-authentication already required by the less-destructive `PATCH /api/users/password` and `POST /api/users/2fa/disable`. 

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
    public class EraseUserDataExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var eraseUserDataRequest = new EraseUserDataRequest(); // EraseUserDataRequest | 

            try
            {
                // Delete user data (GDPR Article 17)
                EraseUserData200Response result = apiInstance.EraseUserData(eraseUserDataRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.EraseUserData: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the EraseUserDataWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete user data (GDPR Article 17)
    ApiResponse<EraseUserData200Response> response = apiInstance.EraseUserDataWithHttpInfo(eraseUserDataRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.EraseUserDataWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **eraseUserDataRequest** | [**EraseUserDataRequest**](EraseUserDataRequest.md) |  |  |

### Return type

[**EraseUserData200Response**](EraseUserData200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account erased |  -  |
| **400** | Missing/invalid confirm, currentPassword, or totpToken |  -  |
| **401** | Authentication required |  -  |
| **409** | Sole owner of one or more organizations - transfer or delete them first |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="exportuserdata"></a>
# **ExportUserData**
> ExportUserData200Response ExportUserData ()

Export user data (GDPR Article 15)

Export all user data in JSON format for GDPR data portability compliance. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 

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
    public class ExportUserDataExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // Export user data (GDPR Article 15)
                ExportUserData200Response result = apiInstance.ExportUserData();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.ExportUserData: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ExportUserDataWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Export user data (GDPR Article 15)
    ApiResponse<ExportUserData200Response> response = apiInstance.ExportUserDataWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.ExportUserDataWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ExportUserData200Response**](ExportUserData200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User data export |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getcurrentuser"></a>
# **GetCurrentUser**
> GetCurrentUser200Response GetCurrentUser ()

Get current user profile

Get the current authenticated user's profile. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). 

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
    public class GetCurrentUserExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // Get current user profile
                GetCurrentUser200Response result = apiInstance.GetCurrentUser();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.GetCurrentUser: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetCurrentUserWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get current user profile
    ApiResponse<GetCurrentUser200Response> response = apiInstance.GetCurrentUserWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.GetCurrentUserWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**GetCurrentUser200Response**](GetCurrentUser200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User profile |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="linkoauthprovider"></a>
# **LinkOAuthProvider**
> void LinkOAuthProvider (string provider, string? projectId = null)

Link OAuth provider to account

Initiate OAuth flow to link a new provider to the current account. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 

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
    public class LinkOAuthProviderExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var provider = google;  // string | 
            var projectId = 685ad30be129932fbb7a1047;  // string? |  (optional) 

            try
            {
                // Link OAuth provider to account
                apiInstance.LinkOAuthProvider(provider, projectId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.LinkOAuthProvider: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the LinkOAuthProviderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Link OAuth provider to account
    apiInstance.LinkOAuthProviderWithHttpInfo(provider, projectId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.LinkOAuthProviderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |
| **projectId** | **string?** |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirect to OAuth provider |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listoauthproviders"></a>
# **ListOAuthProviders**
> ListOAuthProviders200Response ListOAuthProviders ()

List linked OAuth providers

Get all OAuth providers linked to the current user's account. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 

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
    public class ListOAuthProvidersExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // List linked OAuth providers
                ListOAuthProviders200Response result = apiInstance.ListOAuthProviders();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.ListOAuthProviders: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListOAuthProvidersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List linked OAuth providers
    ApiResponse<ListOAuthProviders200Response> response = apiInstance.ListOAuthProvidersWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.ListOAuthProvidersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ListOAuthProviders200Response**](ListOAuthProviders200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of linked OAuth providers |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="resendverificationemail"></a>
# **ResendVerificationEmail**
> MessageResponse ResendVerificationEmail ()

Resend verification email

Sends a new verification email to the authenticated user. Rate limited (e.g. 3 requests per 15 minutes per user). For project-scoped users the link includes project context. 

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
    public class ResendVerificationEmailExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // Resend verification email
                MessageResponse result = apiInstance.ResendVerificationEmail();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.ResendVerificationEmail: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ResendVerificationEmailWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Resend verification email
    ApiResponse<MessageResponse> response = apiInstance.ResendVerificationEmailWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.ResendVerificationEmailWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
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
| **200** | Verification email sent |  -  |
| **400** | Email already verified |  -  |
| **429** | Too many requests (rate limit) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="setup2fa"></a>
# **Setup2FA**
> TwoFASetupResponse Setup2FA ()

Setup 2FA

Setup two-factor authentication for the current user. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

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
    public class Setup2FAExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);

            try
            {
                // Setup 2FA
                TwoFASetupResponse result = apiInstance.Setup2FA();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.Setup2FA: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the Setup2FAWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Setup 2FA
    ApiResponse<TwoFASetupResponse> response = apiInstance.Setup2FAWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.Setup2FAWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**TwoFASetupResponse**](TwoFASetupResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA setup data |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="unlinkoauthprovider"></a>
# **UnlinkOAuthProvider**
> UnlinkOAuthProvider200Response UnlinkOAuthProvider (string provider)

Unlink OAuth provider

Remove an OAuth provider from the current account. Cannot unlink if it's the only authentication method. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

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
    public class UnlinkOAuthProviderExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var provider = github;  // string | 

            try
            {
                // Unlink OAuth provider
                UnlinkOAuthProvider200Response result = apiInstance.UnlinkOAuthProvider(provider);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.UnlinkOAuthProvider: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UnlinkOAuthProviderWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Unlink OAuth provider
    ApiResponse<UnlinkOAuthProvider200Response> response = apiInstance.UnlinkOAuthProviderWithHttpInfo(provider);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.UnlinkOAuthProviderWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |

### Return type

[**UnlinkOAuthProvider200Response**](UnlinkOAuthProvider200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Provider unlinked successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateuserprofile"></a>
# **UpdateUserProfile**
> UpdateUserProfile200Response UpdateUserProfile (UpdateUserRequest updateUserRequest)

Update user profile

Update the current user's profile. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 

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
    public class UpdateUserProfileExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var updateUserRequest = new UpdateUserRequest(); // UpdateUserRequest | 

            try
            {
                // Update user profile
                UpdateUserProfile200Response result = apiInstance.UpdateUserProfile(updateUserRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.UpdateUserProfile: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateUserProfileWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update user profile
    ApiResponse<UpdateUserProfile200Response> response = apiInstance.UpdateUserProfileWithHttpInfo(updateUserRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.UpdateUserProfileWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **updateUserRequest** | [**UpdateUserRequest**](UpdateUserRequest.md) |  |  |

### Return type

[**UpdateUserProfile200Response**](UpdateUserProfile200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Profile updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="verify2fa"></a>
# **Verify2FA**
> MessageResponse Verify2FA (Verify2FARequest verify2FARequest)

Verify and enable 2FA

Verify and enable two-factor authentication for the current user. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 

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
    public class Verify2FAExample
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
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var verify2FARequest = new Verify2FARequest(); // Verify2FARequest | 

            try
            {
                // Verify and enable 2FA
                MessageResponse result = apiInstance.Verify2FA(verify2FARequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.Verify2FA: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the Verify2FAWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Verify and enable 2FA
    ApiResponse<MessageResponse> response = apiInstance.Verify2FAWithHttpInfo(verify2FARequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.Verify2FAWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **verify2FARequest** | [**Verify2FARequest**](Verify2FARequest.md) |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA enabled |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="verifyemail"></a>
# **VerifyEmail**
> MessageResponse VerifyEmail (VerifyEmailAuthRequest verifyEmailAuthRequest)

Verify email address (organization and project)

Verifies the user's email using the token from the link sent at signup. Works for both organization (platform) and project-based signups; the token is from the verification link (e.g. verify-email?token=... for org, or verify-email?token=...&project=... for project). 

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
    public class VerifyEmailExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new UsersApi(httpClient, config, httpClientHandler);
            var verifyEmailAuthRequest = new VerifyEmailAuthRequest(); // VerifyEmailAuthRequest | 

            try
            {
                // Verify email address (organization and project)
                MessageResponse result = apiInstance.VerifyEmail(verifyEmailAuthRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling UsersApi.VerifyEmail: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the VerifyEmailWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Verify email address (organization and project)
    ApiResponse<MessageResponse> response = apiInstance.VerifyEmailWithHttpInfo(verifyEmailAuthRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling UsersApi.VerifyEmailWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **verifyEmailAuthRequest** | [**VerifyEmailAuthRequest**](VerifyEmailAuthRequest.md) |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Email verified |  -  |
| **400** | Invalid verification token |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

