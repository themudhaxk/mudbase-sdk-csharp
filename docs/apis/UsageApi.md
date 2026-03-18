# Mudbase.SDK.Api.UsageApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**UsageGetProject**](UsageApi.md#usagegetproject) | **GET** /api/usage/projects/{projectId} | Get project usage |
| [**UsageGetTrends**](UsageApi.md#usagegettrends) | **GET** /api/usage/trends | Get usage trends |

<a id="usagegetproject"></a>
# **UsageGetProject**
> ProjectUsageStatsResponse UsageGetProject (string projectId, string period = null)

Get project usage

Get usage statistics for a project (API calls, storage, bandwidth, database operations). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to get usage for. |  |
| **period** | **string** | Aggregation period for usage (day, week, or month). | [optional] [default to month] |

### Return type

[**ProjectUsageStatsResponse**](ProjectUsageStatsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project usage statistics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="usagegettrends"></a>
# **UsageGetTrends**
> UsageTrendsResponse UsageGetTrends (int days = null)

Get usage trends

Get usage trends over time for the authenticated organization or project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **days** | **int** | Number of days of trend data to return (default 30). | [optional] [default to 30] |

### Return type

[**UsageTrendsResponse**](UsageTrendsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage trends |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

