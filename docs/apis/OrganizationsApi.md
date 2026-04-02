# Mudbase.SDK.Api.OrganizationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**OrganizationsAddDomain**](OrganizationsApi.md#organizationsadddomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add custom domain |
| [**OrganizationsListDomains**](OrganizationsApi.md#organizationslistdomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS TXT hints |
| [**OrganizationsPatchDomain**](OrganizationsApi.md#organizationspatchdomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Patch domain status or regenerate token |
| [**OrganizationsRemoveDomain**](OrganizationsApi.md#organizationsremovedomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove custom domain |
| [**OrganizationsReportDomainPlatformReady**](OrganizationsApi.md#organizationsreportdomainplatformready) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops hosting / edge ready |
| [**OrganizationsSetPrimaryDomain**](OrganizationsApi.md#organizationssetprimarydomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**OrganizationsVerifyDomainDns**](OrganizationsApi.md#organizationsverifydomaindns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain via DNS TXT |

<a id="organizationsadddomain"></a>
# **OrganizationsAddDomain**
> void OrganizationsAddDomain (string orgId, string projectId, OrganizationsAddDomainRequest organizationsAddDomainRequest)

Add custom domain


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **organizationsAddDomainRequest** | [**OrganizationsAddDomainRequest**](OrganizationsAddDomainRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationslistdomains"></a>
# **OrganizationsListDomains**
> void OrganizationsListDomains (string orgId, string projectId)

List custom domains and DNS TXT hints

Owner/admin. Domains are per project. Returns dnsTxtHost, dnsTxtValue, platformActivationPending (dns_verified waiting for ops), and customDomainLiveForApiTraffic (active or legacy verified). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationspatchdomain"></a>
# **OrganizationsPatchDomain**
> void OrganizationsPatchDomain (string orgId, string projectId, string hostname, OrganizationsPatchDomainRequest organizationsPatchDomainRequest = null)

Patch domain status or regenerate token


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |
| **organizationsPatchDomainRequest** | [**OrganizationsPatchDomainRequest**](OrganizationsPatchDomainRequest.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationsremovedomain"></a>
# **OrganizationsRemoveDomain**
> void OrganizationsRemoveDomain (string orgId, string projectId, string hostname)

Remove custom domain


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Removed |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationsreportdomainplatformready"></a>
# **OrganizationsReportDomainPlatformReady**
> void OrganizationsReportDomainPlatformReady (string orgId, string projectId, string hostname, OrganizationsReportDomainPlatformReadyRequest organizationsReportDomainPlatformReadyRequest = null)

Notify platform ops hosting / edge ready

Legacy optional ops email. First Mudbase TXT success already emails ops. Allowed during platform setup after Mudbase TXT. Recipients default to admin@mudhaxkservices.com and admin@mudbase.dev when CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS is unset. Returns 503 email_provider_not_configured if no email provider is configured. Does not change domain status.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |
| **organizationsReportDomainPlatformReadyRequest** | [**OrganizationsReportDomainPlatformReadyRequest**](OrganizationsReportDomainPlatformReadyRequest.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Ops notified |  -  |
| **400** | custom_domain_invalid_state or other validation |  -  |
| **503** | email_provider_not_configured |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationssetprimarydomain"></a>
# **OrganizationsSetPrimaryDomain**
> void OrganizationsSetPrimaryDomain (string orgId, string projectId, OrganizationsSetPrimaryDomainRequest organizationsSetPrimaryDomainRequest)

Set primary custom domain


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **organizationsSetPrimaryDomainRequest** | [**OrganizationsSetPrimaryDomainRequest**](OrganizationsSetPrimaryDomainRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="organizationsverifydomaindns"></a>
# **OrganizationsVerifyDomainDns**
> void OrganizationsVerifyDomainDns (string orgId, string projectId, string hostname)

Verify domain via DNS TXT

On first success from pending/failed, status becomes cname_pending_staff; ops email once; audit org.domain.txt_verified and org.domain.cname_staff_queued.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Verified; status typically cname_pending_staff after first TXT success |  -  |
| **400** | dns_verification_failed |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

