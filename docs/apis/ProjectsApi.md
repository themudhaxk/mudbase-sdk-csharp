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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createproject"></a>
# **CreateProject**
> CreateProject201Response CreateProject (string orgId, CreateProjectRequest createProjectRequest)

Create new project

Create a new project in an organization. Requires: OrgBearerAuth (organization-level authentication only). 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deleteproject"></a>
# **DeleteProject**
> MessageResponse DeleteProject (string orgId, string id)

Delete project

Delete a project permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getoauthproviderconfig"></a>
# **GetOAuthProviderConfig**
> GetOAuthProviderConfig200Response GetOAuthProviderConfig (string projectId, string provider)

Get OAuth provider configuration

Returns the configuration for a specific OAuth provider for the project (without sensitive data)


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getproject"></a>
# **GetProject**
> Project GetProject (string orgId, string id)

Get single project

Get project details by ID. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectcaptchaconfig"></a>
# **GetProjectCaptchaConfig**
> GetProjectCaptchaConfig200Response GetProjectCaptchaConfig (string orgId, string id)

Get project CAPTCHA configuration

Get CAPTCHA configuration for a project. This is a public endpoint that returns the site key  and settings needed for frontend integration. Secret key is never returned. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectdashboardoverview"></a>
# **GetProjectDashboardOverview**
> ProjectDashboardOverviewResponse GetProjectDashboardOverview (string projectId)

Project dashboard overview

Single response for the project overview UI: project info, request counts and day-over-day % change, active users (distinct JWT users with project activity; realtime socket count when available), **Uptime** (30d headline) is organization-wide when enough HTTP samples exist, else DB heartbeat probes. **Average latency** (today / 7d) is **per project** and counts only routes documented in `openapi-docs.yaml` for customer/project API (excludes auth, `/api/users`, `/api/orgs`, role-elevation, and multi-role admin routes). Request volume and active users remain per-project. 14-day API call volume and recent audit activity are per-project. See docs/dashboard-overview-api.md. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectoauthproviders"></a>
# **GetProjectOAuthProviders**
> GetProjectOAuthProviders200Response GetProjectOAuthProviders (string projectId)

Get configured OAuth providers for a project

Returns a list of OAuth providers that are configured and enabled for the specified project


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectusage"></a>
# **GetProjectUsage**
> ProjectUsageResponse GetProjectUsage (string orgId, string id)

Get project usage statistics


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listprojects"></a>
# **ListProjects**
> ListProjects200Response ListProjects (string orgId)

List all projects

List all projects in an organization. Requires: OrgBearerAuth (organization-level authentication only). 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updateoauthproviderconfig"></a>
# **UpdateOAuthProviderConfig**
> ConfigureOAuthProvider200Response UpdateOAuthProviderConfig (string projectId, string provider, UpdateOAuthProviderConfigRequest updateOAuthProviderConfigRequest)

Update OAuth provider configuration

Updates the configuration for an OAuth provider for the specified project


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updateproject"></a>
# **UpdateProject**
> CreateProject201Response UpdateProject (string orgId, string id, UpdateProjectRequest updateProjectRequest)

Update project

Update project configuration (name, description, settings). **Settings toggles:** **requireEmailVerification** (default true) — when on, new email signups do not get a token until they verify; login is blocked until verified. **requirePhoneVerification** (default false) — when on, phone/OTP users must verify before token. **defaultUserAccountStatus** — **active** (default) or **pending**; when pending, new users must be approved by org owner/admin before they can perform data/storage operations. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="uploadprojectlogo"></a>
# **UploadProjectLogo**
> UploadProjectLogo200Response UploadProjectLogo (string id, System.IO.Stream logo)

Upload project logo (by project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field and used in project-related emails and UI. Project is resolved from the authenticated user's org. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** | Project ID |  |
| **logo** | **System.IO.Stream****System.IO.Stream** | Logo image (PNG, JPEG, GIF, or WebP; max 2MB) |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="uploadprojectlogobyorg"></a>
# **UploadProjectLogoByOrg**
> UploadProjectLogo200Response UploadProjectLogoByOrg (string orgId, string id, System.IO.Stream logo)

Upload project logo (by org and project ID)

Upload a logo image for a project. File is stored in the platform storage under **logo/project/{projectId}/_**. The public URL is saved to the project's **logoUrl** field. Use multipart/form-data with field name **logo**. Allowed types: PNG, JPEG, GIF, WebP. Max size 2MB. Requires project update permission and membership in the organization. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** | Organization ID |  |
| **id** | **string** | Project ID |  |
| **logo** | **System.IO.Stream****System.IO.Stream** | Logo image (PNG, JPEG, GIF, or WebP; max 2MB) |  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

