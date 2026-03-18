# Mudbase.SDK.Api.SearchApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**SearchGetAnalytics**](SearchApi.md#searchgetanalytics) | **GET** /api/search/projects/{projectId}/search/analytics | Get search analytics |
| [**SearchGetSuggestions**](SearchApi.md#searchgetsuggestions) | **GET** /api/search/projects/{projectId}/search/suggestions | Get search suggestions |
| [**SearchSearch**](SearchApi.md#searchsearch) | **GET** /api/search/projects/{projectId}/search | Full-text search |

<a id="searchgetanalytics"></a>
# **SearchGetAnalytics**
> SearchGetAnalytics200Response SearchGetAnalytics (string projectId, string timeframe = null)

Get search analytics

Get search analytics including top queries, search volume, and performance metrics. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to get analytics for. |  |
| **timeframe** | **string** | Timeframe for analytics (1d, 7d, or 30d). | [optional] [default to 7d] |

### Return type

[**SearchGetAnalytics200Response**](SearchGetAnalytics200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search analytics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="searchgetsuggestions"></a>
# **SearchGetSuggestions**
> SearchGetSuggestions200Response SearchGetSuggestions (string projectId, string q, int limit = null)

Get search suggestions

Get search query suggestions based on partial input. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to get suggestions for. |  |
| **q** | **string** | Partial search query (min 2 characters, max 50); suggestions are based on past queries and indexed content. |  |
| **limit** | **int** | Maximum number of suggestions to return (1–20). | [optional] [default to 10] |

### Return type

[**SearchGetSuggestions200Response**](SearchGetSuggestions200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search suggestions |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="searchsearch"></a>
# **SearchSearch**
> SearchResponse SearchSearch (string projectId, string q, string collections = null, string fields = null, int limit = null, int page = null)

Full-text search

Perform full-text search across collections in a project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to search within. |  |
| **q** | **string** | Full-text search query string. |  |
| **collections** | **string** | Comma-separated collection slugs or IDs to limit search scope. | [optional]  |
| **fields** | **string** | Comma-separated field names to search or return in highlights. | [optional]  |
| **limit** | **int** | Maximum number of results to return per page. | [optional] [default to 20] |
| **page** | **int** | Page number for pagination (1-based). | [optional] [default to 1] |

### Return type

[**SearchResponse**](SearchResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search results |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

