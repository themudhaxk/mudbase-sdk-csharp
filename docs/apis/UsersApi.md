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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="changepassword"></a>
# **ChangePassword**
> MessageResponse ChangePassword (ChangePasswordRequest changePasswordRequest)

Change password

Change the current user's password. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="disable2fa"></a>
# **Disable2FA**
> MessageResponse Disable2FA (Disable2FARequest disable2FARequest)

Disable 2FA

Disable two-factor authentication for the current user. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="eraseuserdata"></a>
# **EraseUserData**
> EraseUserData200Response EraseUserData (EraseUserDataRequest eraseUserDataRequest)

Delete user data (GDPR Article 17)

Request account erasure (right to be forgotten). Anonymizes PII, revokes all sessions and API keys, and disables the account immediately (not a grace period - the effect is immediate and irreversible). Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint.  Requires re-proving your current password (skipped only for OAuth-only accounts with no password set) and, if 2FA is enabled, a fresh TOTP code - the same step-up re-authentication already required by the less-destructive `PATCH /api/users/password` and `POST /api/users/2fa/disable`. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="exportuserdata"></a>
# **ExportUserData**
> ExportUserData200Response ExportUserData ()

Export user data (GDPR Article 15)

Export all user data in JSON format for GDPR data portability compliance. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getcurrentuser"></a>
# **GetCurrentUser**
> GetCurrentUser200Response GetCurrentUser ()

Get current user profile

Get the current authenticated user's profile. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="linkoauthprovider"></a>
# **LinkOAuthProvider**
> void LinkOAuthProvider (string provider, string projectId = null)

Link OAuth provider to account

Initiate OAuth flow to link a new provider to the current account. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provider** | **string** |  |  |
| **projectId** | **string** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listoauthproviders"></a>
# **ListOAuthProviders**
> ListOAuthProviders200Response ListOAuthProviders ()

List linked OAuth providers

Get all OAuth providers linked to the current user's account. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="resendverificationemail"></a>
# **ResendVerificationEmail**
> MessageResponse ResendVerificationEmail ()

Resend verification email

Sends a new verification email to the authenticated user. Rate limited (e.g. 3 requests per 15 minutes per user). For project-scoped users the link includes project context. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="setup2fa"></a>
# **Setup2FA**
> TwoFASetupResponse Setup2FA ()

Setup 2FA

Setup two-factor authentication for the current user. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="unlinkoauthprovider"></a>
# **UnlinkOAuthProvider**
> UnlinkOAuthProvider200Response UnlinkOAuthProvider (string provider)

Unlink OAuth provider

Remove an OAuth provider from the current account. Cannot unlink if it's the only authentication method. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updateuserprofile"></a>
# **UpdateUserProfile**
> UpdateUserProfile200Response UpdateUserProfile (UpdateUserRequest updateUserRequest)

Update user profile

Update the current user's profile. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verify2fa"></a>
# **Verify2FA**
> MessageResponse Verify2FA (Verify2FARequest verify2FARequest)

Verify and enable 2FA

Verify and enable two-factor authentication for the current user. Accepts JWT Bearer token (OrgBearerAuth or ProjectBearerAuth - both are the same JWT token format). API keys are not supported for this endpoint. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verifyemail"></a>
# **VerifyEmail**
> MessageResponse VerifyEmail (VerifyEmailAuthRequest verifyEmailAuthRequest)

Verify email address (organization and project)

Verifies the user's email using the token from the link sent at signup. Works for both organization (platform) and project-based signups; the token is from the verification link (e.g. verify-email?token=... for org, or verify-email?token=...&project=... for project). 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

