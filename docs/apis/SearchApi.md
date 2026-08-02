# Mudbase.SDK.Api.SearchApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetSearchAnalytics**](SearchApi.md#getsearchanalytics) | **GET** /api/search/projects/{projectId}/search/analytics | Get search analytics |
| [**GetSearchSuggestions**](SearchApi.md#getsearchsuggestions) | **GET** /api/search/projects/{projectId}/search/suggestions | Get search suggestions |
| [**SearchData**](SearchApi.md#searchdata) | **GET** /api/search/projects/{projectId}/search | Full-text search |

<a id="getsearchanalytics"></a>
# **GetSearchAnalytics**
> GetSearchAnalytics200Response GetSearchAnalytics (string projectId, string timeframe = null)

Get search analytics

Get search analytics including top queries, search volume, and performance metrics. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **timeframe** | **string** |  | [optional] [default to 7d] |

### Return type

[**GetSearchAnalytics200Response**](GetSearchAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search analytics |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getsearchsuggestions"></a>
# **GetSearchSuggestions**
> GetSearchSuggestions200Response GetSearchSuggestions (string projectId, string q, int limit = null)

Get search suggestions

Get search query suggestions based on partial input. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **q** | **string** |  |  |
| **limit** | **int** |  | [optional] [default to 10] |

### Return type

[**GetSearchSuggestions200Response**](GetSearchSuggestions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search suggestions |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="searchdata"></a>
# **SearchData**
> SearchResponse SearchData (string projectId, string q, string collections = null, string fields = null, int limit = null, int page = null)

Full-text search

Perform full-text search across collections in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **q** | **string** |  |  |
| **collections** | **string** |  | [optional]  |
| **fields** | **string** |  | [optional]  |
| **limit** | **int** |  | [optional] [default to 20] |
| **page** | **int** |  | [optional] [default to 1] |

### Return type

[**SearchResponse**](SearchResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Search results |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

