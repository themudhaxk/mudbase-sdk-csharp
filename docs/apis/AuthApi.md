# Mudbase.SDK.Api.AuthApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AuthConfirmPasswordReset**](AuthApi.md#authconfirmpasswordreset) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP |
| [**AuthConvertAnonymous**](AuthApi.md#authconvertanonymous) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**AuthCreateAnonymous**](AuthApi.md#authcreateanonymous) | **POST** /api/auth/anonymous | Create anonymous session |
| [**AuthGetOAuthProviders**](AuthApi.md#authgetoauthproviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**AuthGetSession**](AuthApi.md#authgetsession) | **GET** /api/auth/local/session | Get current session |
| [**AuthLogin**](AuthApi.md#authlogin) | **POST** /api/auth/local/login | Login user |
| [**AuthLogout**](AuthApi.md#authlogout) | **POST** /api/auth/local/logout | Logout user |
| [**AuthOauthCallback**](AuthApi.md#authoauthcallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler |
| [**AuthOauthInitiate**](AuthApi.md#authoauthinitiate) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**AuthRefresh**](AuthApi.md#authrefresh) | **POST** /api/auth/refresh | Refresh access token (org and project) |
| [**AuthRegister**](AuthApi.md#authregister) | **POST** /api/auth/local/register | Register new user |
| [**AuthRequestPasswordReset**](AuthApi.md#authrequestpasswordreset) | **POST** /api/auth/local/password-reset | Request password reset (OTP) |
| [**AuthResendVerification**](AuthApi.md#authresendverification) | **POST** /api/auth/resend-verification | Resend verification email (no auth) |
| [**AuthResetPassword**](AuthApi.md#authresetpassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (legacy) |
| [**AuthSendMagicLink**](AuthApi.md#authsendmagiclink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**AuthSendOtp**](AuthApi.md#authsendotp) | **POST** /api/auth/otp/send | Send OTP code |
| [**AuthVerifyEmail**](AuthApi.md#authverifyemail) | **POST** /api/auth/verify-email | Verify email address (no auth) |
| [**AuthVerifyMagicLink**](AuthApi.md#authverifymagiclink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**AuthVerifyOtp**](AuthApi.md#authverifyotp) | **POST** /api/auth/otp/verify | Verify OTP code |

<a id="authconfirmpasswordreset"></a>
# **AuthConfirmPasswordReset**
> MessageResponse AuthConfirmPasswordReset (AuthConfirmPasswordResetRequest authConfirmPasswordResetRequest)

Confirm password reset with OTP

Set new password using the OTP sent to the user's email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user's email was not yet verified, it is marked as verified upon successful reset. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authConfirmPasswordResetRequest** | [**AuthConfirmPasswordResetRequest**](AuthConfirmPasswordResetRequest.md) | Email, projectId, OTP code, and new password. |  |

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
| **200** | Password reset successful |  -  |
| **400** | Invalid or expired OTP, or validation error |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Too many attempts (rate limit) |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authconvertanonymous"></a>
# **AuthConvertAnonymous**
> AuthConvertAnonymous200Response AuthConvertAnonymous (AuthConvertAnonymousRequest authConvertAnonymousRequest)

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authConvertAnonymousRequest** | [**AuthConvertAnonymousRequest**](AuthConvertAnonymousRequest.md) | Email, password, and optional firstName, lastName for the new full account. |  |

### Return type

[**AuthConvertAnonymous200Response**](AuthConvertAnonymous200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account converted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authcreateanonymous"></a>
# **AuthCreateAnonymous**
> AuthCreateAnonymous200Response AuthCreateAnonymous (AuthCreateAnonymousRequest authCreateAnonymousRequest = null)

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authCreateAnonymousRequest** | [**AuthCreateAnonymousRequest**](AuthCreateAnonymousRequest.md) | Optional projectId and deviceId for the anonymous session. | [optional]  |

### Return type

[**AuthCreateAnonymous200Response**](AuthCreateAnonymous200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Anonymous session created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authgetoauthproviders"></a>
# **AuthGetOAuthProviders**
> AuthGetOAuthProviders200Response AuthGetOAuthProviders ()

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details


### Parameters
This endpoint does not need any parameter.
### Return type

[**AuthGetOAuthProviders200Response**](AuthGetOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authgetsession"></a>
# **AuthGetSession**
> AuthGetSession200Response AuthGetSession (string projectId)

Get current session

Get the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID to get session for. |  |

### Return type

[**AuthGetSession200Response**](AuthGetSession200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authlogin"></a>
# **AuthLogin**
> AuthLogin200Response AuthLogin (AuthLoginRequest authLoginRequest)

Login user

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authLoginRequest** | [**AuthLoginRequest**](AuthLoginRequest.md) | Login credentials (email, password) and project ID. |  |

### Return type

[**AuthLogin200Response**](AuthLogin200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Login successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Email verification required (project has requireEmailVerification and user has not verified) |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authlogout"></a>
# **AuthLogout**
> MessageResponse AuthLogout ()

Logout user

Logout the current authenticated user session. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Logout successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authoauthcallback"></a>
# **AuthOauthCallback**
> AuthOauthCallback200Response AuthOauthCallback (string provider)

OAuth callback handler

OAuth provider redirects the user here after consent. The server exchanges the code for tokens, creates or finds the user, and redirects to the client with token, refreshToken, and expiresIn in query params. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** | OAuth provider identifier (e.g. google, github). |  |

### Return type

[**AuthOauthCallback200Response**](AuthOauthCallback200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (in most cases the server responds with 302 redirect to client with token). |  -  |
| **302** | Redirect with token, refreshToken, and expiresIn |  * Location - URL with token, refreshToken, expiresIn query params <br>  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authoauthinitiate"></a>
# **AuthOauthInitiate**
> AuthOauthInitiate200Response AuthOauthInitiate (string provider, string projectId, string redirectUrl = null)

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. After user authentication, redirects to the OAuth provider's consent screen. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** | OAuth provider identifier (e.g. google, github). |  |
| **projectId** | **string** | Project ID for which OAuth is configured. |  |
| **redirectUrl** | **string** | The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional]  |

### Return type

[**AuthOauthInitiate200Response**](AuthOauthInitiate200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth flow initiated; in most cases the server responds with 302 redirect). |  -  |
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured or not enabled for this project |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authrefresh"></a>
# **AuthRefresh**
> AuthRefresh200Response AuthRefresh (AuthRefreshRequest authRefreshRequest)

Refresh access token (org and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **organization** (platform/dashboard) and **app** auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authRefreshRequest** | [**AuthRefreshRequest**](AuthRefreshRequest.md) | JSON body containing the refresh token to exchange for a new access token and refresh token (token rotation). |  |

### Return type

[**AuthRefresh200Response**](AuthRefresh200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | New token pair issued |  -  |
| **400** | Missing refresh token |  -  |
| **401** | Invalid or expired refresh token (or reuse detected) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authregister"></a>
# **AuthRegister**
> AuthRegister201Response AuthRegister (AuthRegisterRequest authRegisterRequest)

Register new user

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authRegisterRequest** | [**AuthRegisterRequest**](AuthRegisterRequest.md) | Registration payload (email, password, firstName, lastName, projectId). |  |

### Return type

[**AuthRegister201Response**](AuthRegister201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | When project.requireEmailVerification is on (default): no token returned; use requireVerification and message to prompt email verification, then user signs in via login. When off: token and refreshToken returned.  |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authrequestpasswordreset"></a>
# **AuthRequestPasswordReset**
> MessageResponse AuthRequestPasswordReset (AuthRequestPasswordResetRequest authRequestPasswordResetRequest)

Request password reset (OTP)

When projectId is provided, sends a 6-digit OTP to the user's email (app reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authRequestPasswordResetRequest** | [**AuthRequestPasswordResetRequest**](AuthRequestPasswordResetRequest.md) | Email and optional projectId for app OTP or org token link. |  |

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
| **200** | OTP or reset email sent (generic message to prevent enumeration) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Too many requests (rate limit) |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authresendverification"></a>
# **AuthResendVerification**
> MessageResponse AuthResendVerification (AuthResendVerificationRequest authResendVerificationRequest)

Resend verification email (no auth)

Sends a new verification email to the given email (and optional project). For unauthenticated users who have not verified yet. Rate limited (e.g. 3 per 15 min per IP). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authResendVerificationRequest** | [**AuthResendVerificationRequest**](AuthResendVerificationRequest.md) |  |  |

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
| **200** | Verification email sent (or generic message to prevent enumeration) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authresetpassword"></a>
# **AuthResetPassword**
> MessageResponse AuthResetPassword (string token, AuthResetPasswordRequest authResetPasswordRequest)

Reset password with token (legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for app resets. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **token** | **string** | Password reset token from email link. |  |
| **authResetPasswordRequest** | [**AuthResetPasswordRequest**](AuthResetPasswordRequest.md) | New password and optional projectId. |  |

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
| **200** | Password reset successful |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authsendmagiclink"></a>
# **AuthSendMagicLink**
> MessageResponse AuthSendMagicLink (MagicLinkRequest magicLinkRequest)

Send magic link

Sends a one-time magic link to the given email for the project. The user clicks the link and is authenticated without a password. Use verify endpoint with the token from the link. Public endpoint; rate limited. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **magicLinkRequest** | [**MagicLinkRequest**](MagicLinkRequest.md) | Email, projectId, and optional redirect URL for the magic link. |  |

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
| **200** | Magic link sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authsendotp"></a>
# **AuthSendOtp**
> MessageResponse AuthSendOtp (OTPSendRequest oTPSendRequest)

Send OTP code

Sends a one-time code via SMS or email for the given project. Use verify endpoint to exchange the code for a session. Public endpoint; rate limited. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **oTPSendRequest** | [**OTPSendRequest**](OTPSendRequest.md) | Project ID, delivery method (sms/email), and phone or email. |  |

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
| **200** | OTP sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authverifyemail"></a>
# **AuthVerifyEmail**
> MessageResponse AuthVerifyEmail (AuthVerifyEmailRequest authVerifyEmailRequest)

Verify email address (no auth)

Verifies the user's email using the token from the link sent at signup. Use this for both organization and project signups (unauthenticated). Same behavior as POST /api/users/verify-email. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authVerifyEmailRequest** | [**AuthVerifyEmailRequest**](AuthVerifyEmailRequest.md) |  |  |

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
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authverifymagiclink"></a>
# **AuthVerifyMagicLink**
> AuthResponse AuthVerifyMagicLink (AuthVerifyMagicLinkRequest authVerifyMagicLinkRequest)

Verify magic link

Exchanges the magic link token (from the link sent by send) for a session. Returns token and user on success. Token is short-lived and single-use. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authVerifyMagicLinkRequest** | [**AuthVerifyMagicLinkRequest**](AuthVerifyMagicLinkRequest.md) | The token from the magic link URL. |  |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Magic link verified |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="authverifyotp"></a>
# **AuthVerifyOtp**
> AuthResponse AuthVerifyOtp (OTPVerifyRequest oTPVerifyRequest)

Verify OTP code

Verifies the OTP code and returns a session token and user. Public endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **oTPVerifyRequest** | [**OTPVerifyRequest**](OTPVerifyRequest.md) | Identifier (phone/email), OTP code, and project ID. |  |

### Return type

[**AuthResponse**](AuthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | OTP verified |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

