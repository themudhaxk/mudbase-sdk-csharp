# Mudbase.SDK.Api.AuthenticationApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AcceptInvite**](AuthenticationApi.md#acceptinvite) | **POST** /api/auth/accept-invite | Accept organization invitation |
| [**ConfirmLocalPasswordResetWithOtp**](AuthenticationApi.md#confirmlocalpasswordresetwithotp) | **POST** /api/auth/local/password-reset/confirm | Confirm password reset with OTP (project-based) |
| [**ConvertAnonymousAccount**](AuthenticationApi.md#convertanonymousaccount) | **POST** /api/auth/anonymous/convert | Convert anonymous account to full account |
| [**CreateAnonymousSession**](AuthenticationApi.md#createanonymoussession) | **POST** /api/auth/anonymous | Create anonymous session |
| [**GetAvailableOAuthProviders**](AuthenticationApi.md#getavailableoauthproviders) | **GET** /api/auth/oauth/providers/available | Get all available OAuth providers |
| [**GetCurrentSession**](AuthenticationApi.md#getcurrentsession) | **GET** /api/auth/session | Get current session |
| [**GetLocalSession**](AuthenticationApi.md#getlocalsession) | **GET** /api/auth/local/session | Get current session (project-based) |
| [**GetOrgOAuthProviders**](AuthenticationApi.md#getorgoauthproviders) | **GET** /api/auth/oauth-org/providers | Get available OAuth providers for organization-based auth |
| [**InitiateOAuth**](AuthenticationApi.md#initiateoauth) | **GET** /api/auth/oauth/{provider}/{projectId} | Initiate OAuth authentication |
| [**InitiateOrgOAuth**](AuthenticationApi.md#initiateorgoauth) | **GET** /api/auth/oauth-org/{provider} | Initiate OAuth authentication for organization |
| [**LoginLocalUser**](AuthenticationApi.md#loginlocaluser) | **POST** /api/auth/local/login | Login user (project-based) |
| [**LoginUser**](AuthenticationApi.md#loginuser) | **POST** /api/auth/login | Login user |
| [**LogoutLocalUser**](AuthenticationApi.md#logoutlocaluser) | **POST** /api/auth/local/logout | Logout user (project-based) |
| [**LogoutUser**](AuthenticationApi.md#logoutuser) | **POST** /api/auth/logout | Logout user |
| [**OauthCallback**](AuthenticationApi.md#oauthcallback) | **GET** /api/auth/oauth/callback/{provider} | OAuth callback handler (project-based) |
| [**OrgOAuthCallback**](AuthenticationApi.md#orgoauthcallback) | **GET** /api/auth/oauth-org/callback/{provider} | OAuth callback handler for organization |
| [**RefreshToken**](AuthenticationApi.md#refreshtoken) | **POST** /api/auth/refresh | Refresh access token (org and project) |
| [**RegisterLocalUser**](AuthenticationApi.md#registerlocaluser) | **POST** /api/auth/local/register | Register new user (project-based) |
| [**RegisterUser**](AuthenticationApi.md#registeruser) | **POST** /api/auth/register | Register new user |
| [**RequestLocalPasswordReset**](AuthenticationApi.md#requestlocalpasswordreset) | **POST** /api/auth/local/password-reset | Request password reset (project-based, OTP) |
| [**RequestPasswordReset**](AuthenticationApi.md#requestpasswordreset) | **POST** /api/auth/password-reset | Request password reset (organization / platform) |
| [**ResendVerificationAuth**](AuthenticationApi.md#resendverificationauth) | **POST** /api/auth/resend-verification | Resend verification email (no auth) |
| [**ResetLocalPassword**](AuthenticationApi.md#resetlocalpassword) | **POST** /api/auth/local/password-reset/{token} | Reset password with token (project-based, legacy) |
| [**ResetPassword**](AuthenticationApi.md#resetpassword) | **POST** /api/auth/password-reset/{token} | Reset password with token (organization / platform) |
| [**SendMagicLink**](AuthenticationApi.md#sendmagiclink) | **POST** /api/auth/magic-link/send | Send magic link |
| [**SendOTP**](AuthenticationApi.md#sendotp) | **POST** /api/auth/otp/send | Send OTP code |
| [**ValidatePasswordResetToken**](AuthenticationApi.md#validatepasswordresettoken) | **POST** /api/auth/password-reset/validate | Validate password reset token |
| [**VerifyEmailAuth**](AuthenticationApi.md#verifyemailauth) | **POST** /api/auth/verify-email | Verify email address (no auth) |
| [**VerifyMagicLink**](AuthenticationApi.md#verifymagiclink) | **POST** /api/auth/magic-link/verify | Verify magic link |
| [**VerifyOTP**](AuthenticationApi.md#verifyotp) | **POST** /api/auth/otp/verify | Verify OTP code |

<a id="acceptinvite"></a>
# **AcceptInvite**
> AcceptInvite201Response AcceptInvite (AcceptInviteRequest acceptInviteRequest)

Accept organization invitation

Accept an organization invitation using the token from the invite email link (e.g. `/invite/{token}?orgId=...`). Creates a new user with the invited email and adds them to the organization with the invited role. Returns a JWT and user so the client can log the user in immediately. No authentication required. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **acceptInviteRequest** | [**AcceptInviteRequest**](AcceptInviteRequest.md) |  |  |

### Return type

[**AcceptInvite201Response**](AcceptInvite201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Invitation accepted; user created and added to organization |  -  |
| **400** | Invalid or expired token, or user already exists with this email |  -  |
| **404** | Organization not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="confirmlocalpasswordresetwithotp"></a>
# **ConfirmLocalPasswordResetWithOtp**
> MessageResponse ConfirmLocalPasswordResetWithOtp (ConfirmLocalPasswordResetWithOtpRequest confirmLocalPasswordResetWithOtpRequest)

Confirm password reset with OTP (project-based)

Set new password using the OTP sent to the user's email. Call after POST /api/auth/local/password-reset with projectId. Rate limited (OTP limit). If the user's email was not yet verified, it is marked as verified upon successful reset. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **confirmLocalPasswordResetWithOtpRequest** | [**ConfirmLocalPasswordResetWithOtpRequest**](ConfirmLocalPasswordResetWithOtpRequest.md) |  |  |

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
| **404** | Resource not found |  -  |
| **429** | Too many attempts (rate limit) |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="convertanonymousaccount"></a>
# **ConvertAnonymousAccount**
> ConvertAnonymousAccount200Response ConvertAnonymousAccount (ConvertAnonymousAccountRequest convertAnonymousAccountRequest)

Convert anonymous account to full account

Convert an anonymous user session to a full authenticated account. Preserves user data. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **convertAnonymousAccountRequest** | [**ConvertAnonymousAccountRequest**](ConvertAnonymousAccountRequest.md) |  |  |

### Return type

[**ConvertAnonymousAccount200Response**](ConvertAnonymousAccount200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account converted successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createanonymoussession"></a>
# **CreateAnonymousSession**
> CreateAnonymousSession200Response CreateAnonymousSession (CreateAnonymousSessionRequest createAnonymousSessionRequest = null)

Create anonymous session

Create an anonymous user session for guest access. Users can later convert to full accounts.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createAnonymousSessionRequest** | [**CreateAnonymousSessionRequest**](CreateAnonymousSessionRequest.md) |  | [optional]  |

### Return type

[**CreateAnonymousSession200Response**](CreateAnonymousSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Anonymous session created |  -  |
| **400** | Bad request |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getavailableoauthproviders"></a>
# **GetAvailableOAuthProviders**
> GetAvailableOAuthProviders200Response GetAvailableOAuthProviders ()

Get all available OAuth providers

Returns a list of all supported OAuth providers with their configuration details


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetAvailableOAuthProviders200Response**](GetAvailableOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getcurrentsession"></a>
# **GetCurrentSession**
> SessionResponse GetCurrentSession ()

Get current session

Get the current authenticated user session information. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**SessionResponse**](SessionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getlocalsession"></a>
# **GetLocalSession**
> GetLocalSession200Response GetLocalSession (string projectId = null)

Get current session (project-based)

Get the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  | [optional]  |

### Return type

[**GetLocalSession200Response**](GetLocalSession200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current session |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getorgoauthproviders"></a>
# **GetOrgOAuthProviders**
> GetOrgOAuthProviders200Response GetOrgOAuthProviders ()

Get available OAuth providers for organization-based auth

Returns a list of OAuth providers that are configured and available for organization-based authentication. Providers are configured via environment variables (e.g., GOOGLE_CLIENT_ID, GITHUB_CLIENT_ID). 


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetOrgOAuthProviders200Response**](GetOrgOAuthProviders200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of available OAuth providers |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="initiateoauth"></a>
# **InitiateOAuth**
> void InitiateOAuth (string provider, string projectId, string redirectUrl = null)

Initiate OAuth authentication

Initiates OAuth authentication flow for a specified provider and project. The OAuth provider must be configured and enabled for the project first. Returns an HTTP 302 redirect to the OAuth provider's consent screen. Note: Swagger \"Try it out\" may show \"Failed to fetch\" for this endpoint due to browser CORS restrictions on cross-origin redirects. Use top-level browser navigation or curl to test. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |
| **projectId** | **string** |  |  |
| **redirectUrl** | **string** | The URL to redirect to after authentication. Must be pre-registered in project settings. | [optional]  |

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
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured, not enabled, or missing required server/provider credentials |  -  |
| **404** | Project not found |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="initiateorgoauth"></a>
# **InitiateOrgOAuth**
> void InitiateOrgOAuth (string provider, string redirectUrl = null)

Initiate OAuth authentication for organization

Initiates OAuth authentication flow for organization-level signup/login. The OAuth provider must be configured via environment variables (e.g., GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET). After successful authentication, creates a new organization and user account, or logs in existing user. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |
| **redirectUrl** | **string** | The URL to redirect to after authentication | [optional]  |

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
| **302** | Redirect to OAuth provider&#39;s consent screen |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth provider not configured or not supported |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="loginlocaluser"></a>
# **LoginLocalUser**
> LoginLocalUser200Response LoginLocalUser (LoginLocalUserRequest loginLocalUserRequest)

Login user (project-based)

When the project has **requireEmailVerification** enabled and the user has not verified their email, returns 403 with code **EMAIL_VERIFICATION_REQUIRED** (user must verify email first, then login again). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **loginLocalUserRequest** | [**LoginLocalUserRequest**](LoginLocalUserRequest.md) |  |  |

### Return type

[**LoginLocalUser200Response**](LoginLocalUser200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Login successful |  -  |
| **401** | Authentication required |  -  |
| **403** | Email verification required (project has requireEmailVerification and user has not verified) |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="loginuser"></a>
# **LoginUser**
> AuthResponse LoginUser (LoginRequest loginRequest)

Login user


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **loginRequest** | [**LoginRequest**](LoginRequest.md) |  |  |

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
| **200** | Login successful |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="logoutlocaluser"></a>
# **LogoutLocalUser**
> MessageResponse LogoutLocalUser ()

Logout user (project-based)

Logout the current authenticated user session (project-based). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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
| **200** | Logout successful |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="logoutuser"></a>
# **LogoutUser**
> MessageResponse LogoutUser ()

Logout user

Logout the current authenticated user session. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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
| **200** | Logout successful |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="oauthcallback"></a>
# **OauthCallback**
> void OauthCallback (string provider)

OAuth callback handler (project-based)

Handles OAuth callback for project-based authentication. This route must be matched before /api/auth/oauth/{provider}/{projectId}. Redirects to frontend with query params token, refreshToken, and expiresIn. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |

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
| **302** | Redirect with token, refreshToken, and expiresIn |  * Location - URL with token, refreshToken, expiresIn query params <br>  |
| **400** | Bad request |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="orgoauthcallback"></a>
# **OrgOAuthCallback**
> void OrgOAuthCallback (string provider, string code = null, string state = null)

OAuth callback handler for organization

Handles OAuth callback for organization-based authentication. Creates a new organization and user account if the user doesn't exist, or logs in existing user. Redirects to frontend with query params token, refreshToken, and expiresIn. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |
| **code** | **string** | Authorization code from OAuth provider | [optional]  |
| **state** | **string** | State parameter for CSRF protection | [optional]  |

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
| **302** | Redirect with authentication result |  * Location - OAuth provider authorization URL <br>  |
| **400** | OAuth authentication failed |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="refreshtoken"></a>
# **RefreshToken**
> RefreshToken200Response RefreshToken (RefreshTokenRequest refreshTokenRequest)

Refresh access token (org and project)

Exchange a valid refresh token for a new JWT access token and refresh token. Works for both **org-based** (platform/dashboard) and **project-based** auth; the same endpoint is used. The previous refresh token is invalidated (rotation). If the same refresh token is used again, the session is revoked (reuse detection). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **refreshTokenRequest** | [**RefreshTokenRequest**](RefreshTokenRequest.md) |  |  |

### Return type

[**RefreshToken200Response**](RefreshToken200Response.md)

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

<a id="registerlocaluser"></a>
# **RegisterLocalUser**
> RegisterLocalUser201Response RegisterLocalUser (RegisterLocalUserRequest registerLocalUserRequest)

Register new user (project-based)

When the project has **requireEmailVerification** enabled (default), the response is 201 with **requireVerification: true** and **no token**; the user must verify their email then sign in via login. When email verification is disabled, a token and refreshToken are returned. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **registerLocalUserRequest** | [**RegisterLocalUserRequest**](RegisterLocalUserRequest.md) |  |  |

### Return type

[**RegisterLocalUser201Response**](RegisterLocalUser201Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | When project.requireEmailVerification is on (default): no token returned; use requireVerification and message to prompt email verification, then user signs in via login. When off: token and refreshToken returned.  |  -  |
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="registeruser"></a>
# **RegisterUser**
> AuthResponse RegisterUser (RegisterRequest registerRequest)

Register new user


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **registerRequest** | [**RegisterRequest**](RegisterRequest.md) |  |  |

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
| **201** | User registered successfully |  -  |
| **400** | Bad request |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="requestlocalpasswordreset"></a>
# **RequestLocalPasswordReset**
> MessageResponse RequestLocalPasswordReset (RequestLocalPasswordResetRequest requestLocalPasswordResetRequest)

Request password reset (project-based, OTP)

When projectId is provided, sends a 6-digit OTP to the user's email (project-based reset uses OTP, not link). When projectId is omitted, sends a token link (org/platform local account). Rate limited. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **requestLocalPasswordResetRequest** | [**RequestLocalPasswordResetRequest**](RequestLocalPasswordResetRequest.md) |  |  |

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
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |
| **429** | Too many requests (rate limit) |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="requestpasswordreset"></a>
# **RequestPasswordReset**
> MessageResponse RequestPasswordReset (RequestPasswordResetRequest requestPasswordResetRequest)

Request password reset (organization / platform)

Sends a password reset link to the user's email. Use this for organization (platform) accounts. For project-based accounts use POST /api/auth/local/password-reset with projectId (sends OTP instead). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **requestPasswordResetRequest** | [**RequestPasswordResetRequest**](RequestPasswordResetRequest.md) |  |  |

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
| **200** | Password reset email sent (or generic message to prevent enumeration) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="resendverificationauth"></a>
# **ResendVerificationAuth**
> MessageResponse ResendVerificationAuth (ResendVerificationAuthRequest resendVerificationAuthRequest)

Resend verification email (no auth)

Sends a new verification email to the given email (and optional project). For unauthenticated users who have not verified yet. Rate limited (e.g. 3 per 15 min per IP). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **resendVerificationAuthRequest** | [**ResendVerificationAuthRequest**](ResendVerificationAuthRequest.md) |  |  |

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
| **400** | Email required |  -  |
| **429** | Too many requests (rate limit) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="resetlocalpassword"></a>
# **ResetLocalPassword**
> MessageResponse ResetLocalPassword (string token, ResetLocalPasswordRequest resetLocalPasswordRequest)

Reset password with token (project-based, legacy)

Legacy token-based completion. Prefer OTP flow: use POST .../password-reset/confirm with the OTP sent to email for project-based resets. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **token** | **string** |  |  |
| **resetLocalPasswordRequest** | [**ResetLocalPasswordRequest**](ResetLocalPasswordRequest.md) |  |  |

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
| **400** | Bad request |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="resetpassword"></a>
# **ResetPassword**
> MessageResponse ResetPassword (string token, ResetPasswordRequest resetPasswordRequest)

Reset password with token (organization / platform)

Set new password using the token from the reset link. Validate the token first with POST /api/auth/password-reset/validate before showing the form. If the user's email was not yet verified, it is marked as verified upon successful reset. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **token** | **string** |  |  |
| **resetPasswordRequest** | [**ResetPasswordRequest**](ResetPasswordRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="sendmagiclink"></a>
# **SendMagicLink**
> MessageResponse SendMagicLink (MagicLinkRequest magicLinkRequest)

Send magic link


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **magicLinkRequest** | [**MagicLinkRequest**](MagicLinkRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="sendotp"></a>
# **SendOTP**
> MessageResponse SendOTP (OTPSendRequest oTPSendRequest)

Send OTP code


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **oTPSendRequest** | [**OTPSendRequest**](OTPSendRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="validatepasswordresettoken"></a>
# **ValidatePasswordResetToken**
> ValidatePasswordResetToken200Response ValidatePasswordResetToken (ValidatePasswordResetTokenRequest validatePasswordResetTokenRequest)

Validate password reset token

Call before showing the \"set new password\" form. Validates that the token from the reset link is still valid and not expired. Organization (platform) reset only. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **validatePasswordResetTokenRequest** | [**ValidatePasswordResetTokenRequest**](ValidatePasswordResetTokenRequest.md) |  |  |

### Return type

[**ValidatePasswordResetToken200Response**](ValidatePasswordResetToken200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Token is valid |  -  |
| **400** | Token invalid or expired |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verifyemailauth"></a>
# **VerifyEmailAuth**
> MessageResponse VerifyEmailAuth (VerifyEmailAuthRequest verifyEmailAuthRequest)

Verify email address (no auth)

Verifies the user's email using the token from the link sent at signup. Use this for both organization and project signups (unauthenticated). Same behavior as POST /api/users/verify-email. 


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
| **400** | Invalid or missing token |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verifymagiclink"></a>
# **VerifyMagicLink**
> AuthResponse VerifyMagicLink (VerifyMagicLinkRequest verifyMagicLinkRequest)

Verify magic link


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **verifyMagicLinkRequest** | [**VerifyMagicLinkRequest**](VerifyMagicLinkRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verifyotp"></a>
# **VerifyOTP**
> AuthResponse VerifyOTP (OTPVerifyRequest oTPVerifyRequest)

Verify OTP code


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **oTPVerifyRequest** | [**OTPVerifyRequest**](OTPVerifyRequest.md) |  |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

