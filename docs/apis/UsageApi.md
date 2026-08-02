# Mudbase.SDK.Api.UsageApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetOverage**](UsageApi.md#getoverage) | **GET** /api/usage/overage | Get current overage line items |
| [**GetProjectUsageStats**](UsageApi.md#getprojectusagestats) | **GET** /api/usage/projects/{projectId} | Get project usage |
| [**GetProjectUsageSummary**](UsageApi.md#getprojectusagesummary) | **GET** /api/usage/projects/{projectId}/summary | Project dashboard usage summary |
| [**GetUsage**](UsageApi.md#getusage) | **GET** /api/usage | Get organization usage |
| [**GetUsageTrends**](UsageApi.md#getusagetrends) | **GET** /api/usage/trends | Get usage trends |
| [**GetUsageWarnings**](UsageApi.md#getusagewarnings) | **GET** /api/usage/warnings | Get usage warnings |

<a id="getoverage"></a>
# **GetOverage**
> GetOverage200Response GetOverage ()

Get current overage line items

Returns overage line items for the authenticated organization's current billing period (current month). Used by dashboards and billing UIs. Requires org-level JWT (authRequired). 


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetOverage200Response**](GetOverage200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Overage line items for current period |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **503** | Service temporarily unavailable. Returned when the organization is restricted (e.g. suspended due to unpaid overage, spend limit exceeded, or API usage limit reached). End-users see a generic message; the real reason is logged server-side only.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectusagestats"></a>
# **GetProjectUsageStats**
> ProjectUsageStatsResponse GetProjectUsageStats (string projectId, string period = null)

Get project usage

Get usage statistics for a project (API calls, storage, bandwidth, database operations). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **period** | **string** |  | [optional] [default to month] |

### Return type

[**ProjectUsageStatsResponse**](ProjectUsageStatsResponse.md)

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

<a id="getprojectusagesummary"></a>
# **GetProjectUsageSummary**
> ProjectUsageSummaryResponse GetProjectUsageSummary (string projectId)

Project dashboard usage summary

Lightweight dashboard metrics for a project: requests today vs yesterday with % change, active users (24h/7d/30d), 7d active-user trend, 14-day request volume series, per-project openapi-docs latency (today/7d), and uptime (30d) from org HTTP non-5xx when enough samples else DB heartbeats. Same auth as GET /api/usage/projects/{projectId} (org JWT, project JWT, or API key scoped to the project). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**ProjectUsageSummaryResponse**](ProjectUsageSummaryResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Summary payload |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getusage"></a>
# **GetUsage**
> UsageStatsResponse GetUsage (string period = null, DateTime startDate = null, DateTime endDate = null)

Get organization usage


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **period** | **string** |  | [optional] [default to month] |
| **startDate** | **DateTime** |  | [optional]  |
| **endDate** | **DateTime** |  | [optional]  |

### Return type

[**UsageStatsResponse**](UsageStatsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage statistics |  -  |
| **503** | Service temporarily unavailable. Returned when the organization is restricted (e.g. suspended due to unpaid overage, spend limit exceeded, or API usage limit reached). End-users see a generic message; the real reason is logged server-side only.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getusagetrends"></a>
# **GetUsageTrends**
> UsageTrendsResponse GetUsageTrends (int days = null)

Get usage trends

Get usage trends over time for the authenticated organization or project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **days** | **int** |  | [optional] [default to 30] |

### Return type

[**UsageTrendsResponse**](UsageTrendsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage trends |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getusagewarnings"></a>
# **GetUsageWarnings**
> GetUsageWarnings200Response GetUsageWarnings ()

Get usage warnings

Returns usage warnings for the authenticated org (e.g. at 80% and 95% of plan limits). Requires org-level JWT.


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetUsageWarnings200Response**](GetUsageWarnings200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage warnings |  -  |
| **400** | Organization required |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

