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

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class CreateMonitoringAlertExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);
            var createMonitoringAlertRequest = new CreateMonitoringAlertRequest(); // CreateMonitoringAlertRequest | 

            try
            {
                // Create monitoring alert
                apiInstance.CreateMonitoringAlert(createMonitoringAlertRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.CreateMonitoringAlert: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateMonitoringAlertWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create monitoring alert
    apiInstance.CreateMonitoringAlertWithHttpInfo(createMonitoringAlertRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.CreateMonitoringAlertWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringanalytics"></a>
# **GetMonitoringAnalytics**
> MonitoringAnalyticsResponse GetMonitoringAnalytics (string? projectId = null, string? period = null, string? granularity = null, int? days = null)

Get usage analytics (time series)

Aggregates UsageStat by day/week/month. Optional **projectId** scopes to one project. Query **days** (1–90) for a rolling window (e.g. **days=14**); when set, overrides **period**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringAnalyticsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string? |  (optional) 
            var period = "day";  // string? |  (optional)  (default to month)
            var granularity = "day";  // string? |  (optional)  (default to day)
            var days = 56;  // int? | Rolling window in days (1–90); when set, period becomes last_N_days (optional) 

            try
            {
                // Get usage analytics (time series)
                MonitoringAnalyticsResponse result = apiInstance.GetMonitoringAnalytics(projectId, period, granularity, days);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringAnalytics: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringAnalyticsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get usage analytics (time series)
    ApiResponse<MonitoringAnalyticsResponse> response = apiInstance.GetMonitoringAnalyticsWithHttpInfo(projectId, period, granularity, days);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringAnalyticsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string?** |  | [optional]  |
| **period** | **string?** |  | [optional] [default to month] |
| **granularity** | **string?** |  | [optional] [default to day] |
| **days** | **int?** | Rolling window in days (1–90); when set, period becomes last_N_days | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringerrors"></a>
# **GetMonitoringErrors**
> void GetMonitoringErrors ()

Get error logs

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringErrorsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);

            try
            {
                // Get error logs
                apiInstance.GetMonitoringErrors();
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringErrors: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringErrorsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get error logs
    apiInstance.GetMonitoringErrorsWithHttpInfo();
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringErrorsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringlatencyinsights"></a>
# **GetMonitoringLatencyInsights**
> void GetMonitoringLatencyInsights ()

Latency insights (route templates, percentiles, impact scores)

Per-process snapshot: normalized **routeKey** (METHOD + path template), **p50/p95/p99**, 4xx/5xx counts, **impactScore**, **alertsSuggested**, **rps**, **inFlight**, **eventLoopLagP99Ms**. One buffer per server instance. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringLatencyInsightsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);

            try
            {
                // Latency insights (route templates, percentiles, impact scores)
                apiInstance.GetMonitoringLatencyInsights();
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringLatencyInsights: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringLatencyInsightsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Latency insights (route templates, percentiles, impact scores)
    apiInstance.GetMonitoringLatencyInsightsWithHttpInfo();
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringLatencyInsightsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringlogs"></a>
# **GetMonitoringLogs**
> MonitoringLogsResponse GetMonitoringLogs (int? page = null, int? limit = null, string? projectId = null, string? userId = null, string? level = null, DateTime? startDate = null, DateTime? endDate = null, string? action = null, string? resource = null)

Get audit logs

Paginated audit trail for the org. Use **projectId** to scope to one project; **level=all** or **audit** for full activity feed. Each entry includes **activityTitle** and **activityDetail** for dashboard copy. Requires monitoring read permission. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringLogsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);
            var page = 1;  // int? |  (optional)  (default to 1)
            var limit = 20;  // int? |  (optional)  (default to 20)
            var projectId = "projectId_example";  // string? | Filter to this project (must belong to org) (optional) 
            var userId = "userId_example";  // string? | Filter to this user's audit entries (optional) 
            var level = "\"error\"";  // string? | error|security|all|audit|low|medium|high|critical (optional)  (default to "error")
            var startDate = DateTime.Parse("2013-10-20T19:20:30+01:00");  // DateTime? |  (optional) 
            var endDate = DateTime.Parse("2013-10-20T19:20:30+01:00");  // DateTime? |  (optional) 
            var action = "action_example";  // string? |  (optional) 
            var resource = "resource_example";  // string? |  (optional) 

            try
            {
                // Get audit logs
                MonitoringLogsResponse result = apiInstance.GetMonitoringLogs(page, limit, projectId, userId, level, startDate, endDate, action, resource);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringLogs: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringLogsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get audit logs
    ApiResponse<MonitoringLogsResponse> response = apiInstance.GetMonitoringLogsWithHttpInfo(page, limit, projectId, userId, level, startDate, endDate, action, resource);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringLogsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **page** | **int?** |  | [optional] [default to 1] |
| **limit** | **int?** |  | [optional] [default to 20] |
| **projectId** | **string?** | Filter to this project (must belong to org) | [optional]  |
| **userId** | **string?** | Filter to this user&#39;s audit entries | [optional]  |
| **level** | **string?** | error|security|all|audit|low|medium|high|critical | [optional] [default to &quot;error&quot;] |
| **startDate** | **DateTime?** |  | [optional]  |
| **endDate** | **DateTime?** |  | [optional]  |
| **action** | **string?** |  | [optional]  |
| **resource** | **string?** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringperformance"></a>
# **GetMonitoringPerformance**
> MonitoringPerformanceResponse GetMonitoringPerformance (string? projectId = null, string? period = null)

Get performance metrics

Response time stats from AuditLog where available. With **projectId**, falls back to UsageStat latency averages when audit data is sparse (**latencySource** may be **usage_stat**). 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringPerformanceExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string? |  (optional) 
            var period = "hour";  // string? |  (optional)  (default to hour)

            try
            {
                // Get performance metrics
                MonitoringPerformanceResponse result = apiInstance.GetMonitoringPerformance(projectId, period);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringPerformance: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringPerformanceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get performance metrics
    ApiResponse<MonitoringPerformanceResponse> response = apiInstance.GetMonitoringPerformanceWithHttpInfo(projectId, period);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringPerformanceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string?** |  | [optional]  |
| **period** | **string?** |  | [optional] [default to hour] |

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getmonitoringqueuemetrics"></a>
# **GetMonitoringQueueMetrics**
> void GetMonitoringQueueMetrics ()

Usage metering queue job counts

BullMQ **usage-events** queue counts when `USE_METERING_QUEUE` and `REDIS_URL` are set.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetMonitoringQueueMetricsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);

            try
            {
                // Usage metering queue job counts
                apiInstance.GetMonitoringQueueMetrics();
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetMonitoringQueueMetrics: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetMonitoringQueueMetricsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Usage metering queue job counts
    apiInstance.GetMonitoringQueueMetricsWithHttpInfo();
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetMonitoringQueueMetricsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getscannermetrics"></a>
# **GetScannerMetrics**
> GetScannerMetrics200Response GetScannerMetrics ()

Get block scanner metrics

Returns per-chain block scanner lag and health. Used for observability of ETH/UTXO block-based wallet monitoring. Alerts when lag exceeds threshold.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class GetScannerMetricsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);

            try
            {
                // Get block scanner metrics
                GetScannerMetrics200Response result = apiInstance.GetScannerMetrics();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.GetScannerMetrics: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetScannerMetricsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get block scanner metrics
    ApiResponse<GetScannerMetrics200Response> response = apiInstance.GetScannerMetricsWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.GetScannerMetricsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listmonitoringalerts"></a>
# **ListMonitoringAlerts**
> void ListMonitoringAlerts ()

List monitoring alerts

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class ListMonitoringAlertsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new MonitoringApi(httpClient, config, httpClientHandler);

            try
            {
                // List monitoring alerts
                apiInstance.ListMonitoringAlerts();
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MonitoringApi.ListMonitoringAlerts: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListMonitoringAlertsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List monitoring alerts
    apiInstance.ListMonitoringAlertsWithHttpInfo();
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MonitoringApi.ListMonitoringAlertsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

