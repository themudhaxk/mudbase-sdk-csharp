# Mudbase.SDK.Api.MonitoringApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateMonitoringAlert**](MonitoringApi.md#createmonitoringalert) | **POST** /api/monitoring/alerts | Create monitoring alert |
| [**GetMonitoringAnalytics**](MonitoringApi.md#getmonitoringanalytics) | **GET** /api/monitoring/analytics | Get usage analytics (time series) |
| [**GetMonitoringErrors**](MonitoringApi.md#getmonitoringerrors) | **GET** /api/monitoring/errors | Get error logs |
| [**GetMonitoringLatencyInsights**](MonitoringApi.md#getmonitoringlatencyinsights) | **GET** /api/monitoring/latency-insights | Latency insights (route templates, percentiles, impact scores) |
| [**GetMonitoringLogs**](MonitoringApi.md#getmonitoringlogs) | **GET** /api/monitoring/logs | Get audit logs |
| [**GetMonitoringPerformance**](MonitoringApi.md#getmonitoringperformance) | **GET** /api/monitoring/performance | Get performance metrics |
| [**GetMonitoringQueueMetrics**](MonitoringApi.md#getmonitoringqueuemetrics) | **GET** /api/monitoring/queue-metrics | Usage metering queue job counts |
| [**GetScannerMetrics**](MonitoringApi.md#getscannermetrics) | **GET** /api/monitoring/scanner-metrics | Get block scanner metrics |
| [**ListMonitoringAlerts**](MonitoringApi.md#listmonitoringalerts) | **GET** /api/monitoring/alerts | List monitoring alerts |

<a id="createmonitoringalert"></a>
# **CreateMonitoringAlert**
> void CreateMonitoringAlert (CreateMonitoringAlertRequest createMonitoringAlertRequest)

Create monitoring alert

Create a monitoring alert (plan limit alertsPerProject enforced).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createMonitoringAlertRequest** | [**CreateMonitoringAlertRequest**](CreateMonitoringAlertRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Alert created |  -  |
| **401** | Authentication required |  -  |
| **403** | Alert limit reached for your plan |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringanalytics"></a>
# **GetMonitoringAnalytics**
> MonitoringAnalyticsResponse GetMonitoringAnalytics (string projectId = null, string period = null, string granularity = null, int days = null)

Get usage analytics (time series)

Aggregates UsageStat by day/week/month. Optional **projectId** scopes to one project. Query **days** (1–90) for a rolling window (e.g. **days=14**); when set, overrides **period**. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  | [optional]  |
| **period** | **string** |  | [optional] [default to month] |
| **granularity** | **string** |  | [optional] [default to day] |
| **days** | **int** | Rolling window in days (1–90); when set, period becomes last_N_days | [optional]  |

### Return type

[**MonitoringAnalyticsResponse**](MonitoringAnalyticsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Stats series and totals |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringerrors"></a>
# **GetMonitoringErrors**
> void GetMonitoringErrors ()

Get error logs


### Parameters
This endpoint does not need any parameter.
### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Error logs |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringlatencyinsights"></a>
# **GetMonitoringLatencyInsights**
> void GetMonitoringLatencyInsights ()

Latency insights (route templates, percentiles, impact scores)

Per-process snapshot: normalized **routeKey** (METHOD + path template), **p50/p95/p99**, 4xx/5xx counts, **impactScore**, **alertsSuggested**, **rps**, **inFlight**, **eventLoopLagP99Ms**. One buffer per server instance. 


### Parameters
This endpoint does not need any parameter.
### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Latency insights payload |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringlogs"></a>
# **GetMonitoringLogs**
> MonitoringLogsResponse GetMonitoringLogs (int page = null, int limit = null, string projectId = null, string userId = null, string level = null, DateTime startDate = null, DateTime endDate = null, string action = null, string resource = null)

Get audit logs

Paginated audit trail for the org. Use **projectId** to scope to one project; **level=all** or **audit** for full activity feed. Each entry includes **activityTitle** and **activityDetail** for dashboard copy. Requires monitoring read permission. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |
| **projectId** | **string** | Filter to this project (must belong to org) | [optional]  |
| **userId** | **string** | Filter to this user&#39;s audit entries | [optional]  |
| **level** | **string** | error|security|all|audit|low|medium|high|critical | [optional] [default to &quot;error&quot;] |
| **startDate** | **DateTime** |  | [optional]  |
| **endDate** | **DateTime** |  | [optional]  |
| **action** | **string** |  | [optional]  |
| **resource** | **string** |  | [optional]  |

### Return type

[**MonitoringLogsResponse**](MonitoringLogsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Audit logs with pagination |  -  |
| **400** | Invalid userId format |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringperformance"></a>
# **GetMonitoringPerformance**
> MonitoringPerformanceResponse GetMonitoringPerformance (string projectId = null, string period = null)

Get performance metrics

Response time stats from AuditLog where available. With **projectId**, falls back to UsageStat latency averages when audit data is sparse (**latencySource** may be **usage_stat**). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  | [optional]  |
| **period** | **string** |  | [optional] [default to hour] |

### Return type

[**MonitoringPerformanceResponse**](MonitoringPerformanceResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Performance metrics |  -  |
| **401** | Authentication required |  -  |
| **404** | Project not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getmonitoringqueuemetrics"></a>
# **GetMonitoringQueueMetrics**
> void GetMonitoringQueueMetrics ()

Usage metering queue job counts

BullMQ **usage-events** queue counts when `USE_METERING_QUEUE` and `REDIS_URL` are set.


### Parameters
This endpoint does not need any parameter.
### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Queue depth snapshot |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getscannermetrics"></a>
# **GetScannerMetrics**
> GetScannerMetrics200Response GetScannerMetrics ()

Get block scanner metrics

Returns per-chain block scanner lag and health. Used for observability of ETH/UTXO block-based wallet monitoring. Alerts when lag exceeds threshold.


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetScannerMetrics200Response**](GetScannerMetrics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Scanner metrics and optional lag alerts |  -  |
| **401** | Authentication required |  -  |
| **500** | Failed to fetch scanner metrics |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listmonitoringalerts"></a>
# **ListMonitoringAlerts**
> void ListMonitoringAlerts ()

List monitoring alerts


### Parameters
This endpoint does not need any parameter.
### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of alerts |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

