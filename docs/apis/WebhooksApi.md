# Mudbase.SDK.Api.WebhooksApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**WebhooksGetStats**](WebhooksApi.md#webhooksgetstats) | **GET** /api/webhooks/stats | Get webhook statistics |

<a id="webhooksgetstats"></a>
# **WebhooksGetStats**
> WebhookStatsResponse WebhooksGetStats (string projectId = null, int days = null)

Get webhook statistics

Get webhook delivery statistics including success rate, total deliveries, and breakdown by status. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID to filter stats (optional). | [optional]  |
| **days** | **int** | Number of days to include in the stats window. | [optional] [default to 7] |

### Return type

[**WebhookStatsResponse**](WebhookStatsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook statistics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

