# Mudbase.SDK.Api.MultiRoleApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AuthOauthSignupWithRole**](MultiRoleApi.md#authoauthsignupwithrole) | **GET** /api/auth/oauth/signup/{role}/{provider}/{projectId} | OAuth signup with specific role |
| [**AuthRegisterWithRole**](MultiRoleApi.md#authregisterwithrole) | **POST** /api/auth/local/signup/{role} | Register user with specific role (Local Auth) |

<a id="authoauthsignupwithrole"></a>
# **AuthOauthSignupWithRole**
> UsersLinkOAuthProvider200Response AuthOauthSignupWithRole (string role, string provider, string projectId, string redirectUrl = null)

OAuth signup with specific role

Public endpoint that initiates OAuth signup flow with a specific role assigned during registration. The OAuth provider must be configured and enabled for the project first. The role must be available for signup in the project's multi-role configuration. After successful OAuth authentication, the user will be created with the specified role. No authentication required - this is a public signup endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **role** | **string** | Path segment must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; use each role&#39;s configured endpoint). |  |
| **provider** | **string** | OAuth provider (e.g. google, github). |  |
| **projectId** | **string** | Project ID. |  |
| **redirectUrl** | **string** | The URL to redirect to after authentication | [optional]  |

### Return type

[**UsersLinkOAuthProvider200Response**](UsersLinkOAuthProvider200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth signup flow initiated; in most cases the server responds with 302 redirect). |  -  |
| **302** | Redirects to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, role not found, or validation error |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authregisterwithrole"></a>
# **AuthRegisterWithRole**
> void AuthRegisterWithRole (string role, AuthRegisterWithRoleRequest authRegisterWithRoleRequest)

Register user with specific role (Local Auth)

Public endpoint for user registration with a specific role. The path segment must match a role's `signupEndpoint` (default starter is `customer`; add more roles via multi-role API). No authentication required - this is a public signup endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **role** | **string** | Must match the role&#39;s &#x60;signupEndpoint&#x60; (default &#x60;customer&#x60;; other values for roles you add). |  |
| **authRegisterWithRoleRequest** | [**AuthRegisterWithRoleRequest**](AuthRegisterWithRoleRequest.md) | Registration payload (email, password, firstName, lastName, projectId). |  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Registration successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Role not found or not enabled |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

