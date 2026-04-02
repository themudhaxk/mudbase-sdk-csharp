# Mudbase.SDK.Api.UsersApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**UsersChangePassword**](UsersApi.md#userschangepassword) | **PATCH** /api/users/password | Change password |
| [**UsersDisable2fa**](UsersApi.md#usersdisable2fa) | **POST** /api/users/2fa/disable | Disable 2FA |
| [**UsersEraseData**](UsersApi.md#userserasedata) | **POST** /api/users/me/erase | Delete user data (GDPR Article 17) |
| [**UsersExportData**](UsersApi.md#usersexportdata) | **GET** /api/users/me/export | Export user data (GDPR Article 15) |
| [**UsersGet**](UsersApi.md#usersget) | **GET** /api/users/me | Get current user profile |
| [**UsersLinkOAuthProvider**](UsersApi.md#userslinkoauthprovider) | **GET** /api/users/me/oauth-providers/link/{provider} | Link OAuth provider to account |
| [**UsersListOAuthProviders**](UsersApi.md#userslistoauthproviders) | **GET** /api/users/me/oauth-providers | List linked OAuth providers |
| [**UsersResendVerification**](UsersApi.md#usersresendverification) | **POST** /api/users/resend-verification | Resend verification email |
| [**UsersSetup2fa**](UsersApi.md#userssetup2fa) | **POST** /api/users/2fa/setup | Initiate two-factor authentication setup (secret, QR code, backup codes) |
| [**UsersUnlinkOAuthProvider**](UsersApi.md#usersunlinkoauthprovider) | **DELETE** /api/users/me/oauth-providers/{provider} | Unlink OAuth provider |
| [**UsersUpdate**](UsersApi.md#usersupdate) | **PATCH** /api/users/update | Update user profile |
| [**UsersVerify2fa**](UsersApi.md#usersverify2fa) | **POST** /api/users/2fa/verify | Verify and enable 2FA |
| [**UsersVerifyEmail**](UsersApi.md#usersverifyemail) | **POST** /api/users/verify-email | Verify email address (with optional project context) |

<a id="userschangepassword"></a>
# **UsersChangePassword**
> MessageResponse UsersChangePassword (ChangePasswordRequest changePasswordRequest)

Change password

Change the current user's password. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **changePasswordRequest** | [**ChangePasswordRequest**](ChangePasswordRequest.md) | Current password and new password. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Password changed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersdisable2fa"></a>
# **UsersDisable2fa**
> MessageResponse UsersDisable2fa (UsersDisable2faRequest usersDisable2faRequest)

Disable 2FA

Disable two-factor authentication for the current user. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **usersDisable2faRequest** | [**UsersDisable2faRequest**](UsersDisable2faRequest.md) | Current password and one-time code to confirm disable. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA disabled |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="userserasedata"></a>
# **UsersEraseData**
> UsersEraseData200Response UsersEraseData (UsersEraseDataRequest usersEraseDataRequest)

Delete user data (GDPR Article 17)

Request account erasure (right to be forgotten). Anonymizes PII and deactivates account with 7-day grace period. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **usersEraseDataRequest** | [**UsersEraseDataRequest**](UsersEraseDataRequest.md) | Confirmation string (DELETE_MY_ACCOUNT) and optional reason for erasure. |  |

### Return type

[**UsersEraseData200Response**](UsersEraseData200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Account erasure initiated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersexportdata"></a>
# **UsersExportData**
> UsersExportData200Response UsersExportData ()

Export user data (GDPR Article 15)

Export all user data in JSON format for GDPR data portability compliance. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**UsersExportData200Response**](UsersExportData200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User data export |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersget"></a>
# **UsersGet**
> UsersGet200Response UsersGet ()

Get current user profile

Get the current authenticated user's profile. Accepts JWT Bearer token (BearerToken). 


### Parameters
This endpoint does not need any parameter.
### Return type

[**UsersGet200Response**](UsersGet200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User profile |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="userslinkoauthprovider"></a>
# **UsersLinkOAuthProvider**
> UsersLinkOAuthProvider200Response UsersLinkOAuthProvider (string provider, string projectId = null)

Link OAuth provider to account

Initiate OAuth flow to link a new provider to the current account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** | OAuth provider to link (e.g. google, github). |  |
| **projectId** | **string** | Project ID for the OAuth link context. | [optional]  |

### Return type

[**UsersLinkOAuthProvider200Response**](UsersLinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Success (OAuth link flow initiated; in most cases the server responds with 302 redirect to provider). |  -  |
| **302** | Redirect to OAuth provider |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="userslistoauthproviders"></a>
# **UsersListOAuthProviders**
> UsersListOAuthProviders200Response UsersListOAuthProviders ()

List linked OAuth providers

Get all OAuth providers linked to the current user's account. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**UsersListOAuthProviders200Response**](UsersListOAuthProviders200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of linked OAuth providers |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersresendverification"></a>
# **UsersResendVerification**
> MessageResponse UsersResendVerification ()

Resend verification email

Sends a new verification email to the authenticated user. Rate limited (e.g. 3 requests per 15 minutes per user). For app users the link includes project context. 


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
| **200** | Verification email sent |  -  |
| **400** | Email already verified |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Too many requests (rate limit) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="userssetup2fa"></a>
# **UsersSetup2fa**
> TwoFASetupResponse UsersSetup2fa ()

Initiate two-factor authentication setup (secret, QR code, backup codes)

Initiates two-factor authentication setup for the current user. Returns a secret, QR code, and manual entry key for the user to add to an authenticator app. Requires JWT Bearer token (BearerToken). API keys are not supported. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**TwoFASetupResponse**](TwoFASetupResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA setup data |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersunlinkoauthprovider"></a>
# **UsersUnlinkOAuthProvider**
> UsersUnlinkOAuthProvider200Response UsersUnlinkOAuthProvider (string provider)

Unlink OAuth provider

Remove an OAuth provider from the current account. Cannot unlink if it's the only authentication method. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** | OAuth provider to unlink (e.g. google, github). |  |

### Return type

[**UsersUnlinkOAuthProvider200Response**](UsersUnlinkOAuthProvider200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Provider unlinked successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersupdate"></a>
# **UsersUpdate**
> UsersUpdate200Response UsersUpdate (UpdateUserRequest updateUserRequest)

Update user profile

Update the current user's profile. Requires JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **updateUserRequest** | [**UpdateUserRequest**](UpdateUserRequest.md) | Profile fields to update (firstName, lastName, avatar). |  |

### Return type

[**UsersUpdate200Response**](UsersUpdate200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Profile updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersverify2fa"></a>
# **UsersVerify2fa**
> MessageResponse UsersVerify2fa (UsersVerify2faRequest usersVerify2faRequest)

Verify and enable 2FA

Verify and enable two-factor authentication for the current user. Accepts JWT Bearer token (BearerToken). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **usersVerify2faRequest** | [**UsersVerify2faRequest**](UsersVerify2faRequest.md) | One-time code from the authenticator app. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | 2FA enabled |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usersverifyemail"></a>
# **UsersVerifyEmail**
> MessageResponse UsersVerifyEmail (AuthVerifyEmailRequest authVerifyEmailRequest)

Verify email address (with optional project context)

Verifies the user's email using the token from the link sent at signup. Supports general and project-scoped signups; the token comes from the verification link (e.g. `verify-email?token=...` or `verify-email?token=...&project=...`). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **authVerifyEmailRequest** | [**AuthVerifyEmailRequest**](AuthVerifyEmailRequest.md) | Verification token from the email link; optional projectId for project context. |  |

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
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

