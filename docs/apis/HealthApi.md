# Mudbase.SDK.Api.HealthApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**HealthCheck**](HealthApi.md#healthcheck) | **GET** /health | Health check |
| [**SystemStatus**](HealthApi.md#systemstatus) | **GET** /api/status | System status |

<a id="healthcheck"></a>
# **HealthCheck**
> HealthResponse HealthCheck ()

Health check


### Parameters
This endpoint does not need any parameter.
### Return type

[**HealthResponse**](HealthResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | System health status |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="systemstatus"></a>
# **SystemStatus**
> SystemStatusResponse SystemStatus ()

System status


### Parameters
This endpoint does not need any parameter.
### Return type

[**SystemStatusResponse**](SystemStatusResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Detailed system status |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

