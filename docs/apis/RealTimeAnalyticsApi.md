# Mudbase.SDK.Api.RealTimeAnalyticsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CheckUserPresence**](RealTimeAnalyticsApi.md#checkuserpresence) | **POST** /api/realtime/projects/{projectId}/presence | Check presence status for users |
| [**GetActiveUsers**](RealTimeAnalyticsApi.md#getactiveusers) | **GET** /api/realtime/projects/{projectId}/active-users | Get active users for a project |
| [**GetEventThroughput**](RealTimeAnalyticsApi.md#geteventthroughput) | **GET** /api/realtime/projects/{projectId}/throughput | Get event throughput metrics |
| [**GetGlobalAnalytics**](RealTimeAnalyticsApi.md#getglobalanalytics) | **GET** /api/realtime/analytics | Get global real-time analytics |
| [**GetHistoricalAnalytics**](RealTimeAnalyticsApi.md#gethistoricalanalytics) | **GET** /api/realtime/projects/{projectId}/history | Get historical analytics |
| [**GetProjectAnalytics**](RealTimeAnalyticsApi.md#getprojectanalytics) | **GET** /api/realtime/projects/{projectId}/analytics | Get project real-time analytics |

<a id="checkuserpresence"></a>
# **CheckUserPresence**
> CheckUserPresence200Response CheckUserPresence (string projectId, CheckUserPresenceRequest checkUserPresenceRequest)

Check presence status for users

Returns online status for specified user IDs


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **checkUserPresenceRequest** | [**CheckUserPresenceRequest**](CheckUserPresenceRequest.md) |  |  |

### Return type

[**CheckUserPresence200Response**](CheckUserPresence200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presence status for each user |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getactiveusers"></a>
# **GetActiveUsers**
> GetActiveUsers200Response GetActiveUsers (string projectId)

Get active users for a project

Returns list of currently connected users


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetActiveUsers200Response**](GetActiveUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of active users |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="geteventthroughput"></a>
# **GetEventThroughput**
> GetEventThroughput200Response GetEventThroughput (string projectId, int window = null)

Get event throughput metrics

Returns event throughput for a project


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **window** | **int** | Time window in milliseconds | [optional] [default to 60000] |

### Return type

[**GetEventThroughput200Response**](GetEventThroughput200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Throughput metrics |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getglobalanalytics"></a>
# **GetGlobalAnalytics**
> GetGlobalAnalytics200Response GetGlobalAnalytics ()

Get global real-time analytics

Returns system-wide real-time metrics (admin only)


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetGlobalAnalytics200Response**](GetGlobalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Global analytics data |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="gethistoricalanalytics"></a>
# **GetHistoricalAnalytics**
> GetHistoricalAnalytics200Response GetHistoricalAnalytics (string projectId, string period = null)

Get historical analytics

Returns historical analytics for charting


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **period** | **string** | Time period for historical data | [optional] [default to hour] |

### Return type

[**GetHistoricalAnalytics200Response**](GetHistoricalAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Historical analytics data |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectanalytics"></a>
# **GetProjectAnalytics**
> GetProjectAnalytics200Response GetProjectAnalytics (string projectId)

Get project real-time analytics

Returns real-time metrics for a specific project (active connections, events, etc.)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetProjectAnalytics200Response**](GetProjectAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project analytics data |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

