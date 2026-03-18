# Mudbase.SDK.Api.RealtimeAnalyticsApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**RealtimeAnalyticsCheckUserPresence**](RealtimeAnalyticsApi.md#realtimeanalyticscheckuserpresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**RealtimeAnalyticsGetActiveUsers**](RealtimeAnalyticsApi.md#realtimeanalyticsgetactiveusers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**RealtimeAnalyticsGetEventThroughput**](RealtimeAnalyticsApi.md#realtimeanalyticsgeteventthroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**RealtimeAnalyticsGetHistoricalAnalytics**](RealtimeAnalyticsApi.md#realtimeanalyticsgethistoricalanalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**RealtimeAnalyticsGetProject**](RealtimeAnalyticsApi.md#realtimeanalyticsgetproject) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |

<a id="realtimeanalyticscheckuserpresence"></a>
# **RealtimeAnalyticsCheckUserPresence**
> RealtimeAnalyticsCheckUserPresence200Response RealtimeAnalyticsCheckUserPresence (string projectId, RealtimeAnalyticsCheckUserPresenceRequest realtimeAnalyticsCheckUserPresenceRequest)

Check presence status for users

Returns online status for specified user IDs


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **realtimeAnalyticsCheckUserPresenceRequest** | [**RealtimeAnalyticsCheckUserPresenceRequest**](RealtimeAnalyticsCheckUserPresenceRequest.md) | Array of user IDs to check presence for. |  |

### Return type

[**RealtimeAnalyticsCheckUserPresence200Response**](RealtimeAnalyticsCheckUserPresence200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presence status for each user |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="realtimeanalyticsgetactiveusers"></a>
# **RealtimeAnalyticsGetActiveUsers**
> RealtimeAnalyticsGetActiveUsers200Response RealtimeAnalyticsGetActiveUsers (string projectId)

Get active users for a project

Returns list of currently connected users


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |

### Return type

[**RealtimeAnalyticsGetActiveUsers200Response**](RealtimeAnalyticsGetActiveUsers200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of active users |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="realtimeanalyticsgeteventthroughput"></a>
# **RealtimeAnalyticsGetEventThroughput**
> RealtimeAnalyticsGetEventThroughput200Response RealtimeAnalyticsGetEventThroughput (string projectId, int window = null)

Get event throughput metrics

Returns event throughput for a project


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **window** | **int** | Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**RealtimeAnalyticsGetEventThroughput200Response**](RealtimeAnalyticsGetEventThroughput200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Throughput metrics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="realtimeanalyticsgethistoricalanalytics"></a>
# **RealtimeAnalyticsGetHistoricalAnalytics**
> RealtimeAnalyticsGetHistoricalAnalytics200Response RealtimeAnalyticsGetHistoricalAnalytics (string projectId, string period = null)

Get historical analytics

Returns historical analytics for charting


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **period** | **string** | Time period for historical data | [optional] [default to hour] |

### Return type

[**RealtimeAnalyticsGetHistoricalAnalytics200Response**](RealtimeAnalyticsGetHistoricalAnalytics200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Historical analytics data |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="realtimeanalyticsgetproject"></a>
# **RealtimeAnalyticsGetProject**
> RealtimeAnalyticsGetProject200Response RealtimeAnalyticsGetProject (string projectId)

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to get real-time analytics for. |  |

### Return type

[**RealtimeAnalyticsGetProject200Response**](RealtimeAnalyticsGetProject200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project analytics data |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

