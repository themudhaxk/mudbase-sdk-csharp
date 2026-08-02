# Mudbase.SDK.Api.IntegrationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateFromTemplate**](IntegrationsApi.md#createfromtemplate) | **POST** /api/integrations/projects/{projectId}/integrations/from-template | Create integration from template |
| [**CreateIntegration**](IntegrationsApi.md#createintegration) | **POST** /api/integrations/projects/{projectId}/integrations | Create new integration |
| [**DeleteIntegration**](IntegrationsApi.md#deleteintegration) | **DELETE** /api/integrations/projects/{projectId}/integrations/{integrationId} | Delete integration |
| [**ExecuteIntegration**](IntegrationsApi.md#executeintegration) | **POST** /api/integrations/projects/{projectId}/integrations/{integrationId}/execute | Execute integration |
| [**ExportIntegration**](IntegrationsApi.md#exportintegration) | **GET** /api/integrations/projects/{projectId}/integrations/{integrationId}/export | Export integration |
| [**GetIntegration**](IntegrationsApi.md#getintegration) | **GET** /api/integrations/projects/{projectId}/integrations/{integrationId} | Get integration details |
| [**GetIntegrations**](IntegrationsApi.md#getintegrations) | **GET** /api/integrations/projects/{projectId}/integrations | Get project integrations |
| [**GetTemplates**](IntegrationsApi.md#gettemplates) | **GET** /api/integrations/templates | Get integration templates |
| [**GetUsageStats**](IntegrationsApi.md#getusagestats) | **GET** /api/integrations/projects/{projectId}/integrations/{integrationId}/usage | Get integration usage statistics |
| [**ImportIntegration**](IntegrationsApi.md#importintegration) | **POST** /api/integrations/projects/{projectId}/integrations/import | Import integration |
| [**TestIntegration**](IntegrationsApi.md#testintegration) | **POST** /api/integrations/projects/{projectId}/integrations/{integrationId}/test | Test integration |
| [**UpdateIntegration**](IntegrationsApi.md#updateintegration) | **PATCH** /api/integrations/projects/{projectId}/integrations/{integrationId} | Update integration |

<a id="createfromtemplate"></a>
# **CreateFromTemplate**
> CreateIntegration201Response CreateFromTemplate (string projectId, CreateFromTemplateRequest createFromTemplateRequest)

Create integration from template

Create a new integration using a pre-configured template. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createFromTemplateRequest** | [**CreateFromTemplateRequest**](CreateFromTemplateRequest.md) |  |  |

### Return type

[**CreateIntegration201Response**](CreateIntegration201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Integration created from template |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createintegration"></a>
# **CreateIntegration**
> CreateIntegration201Response CreateIntegration (string projectId, CreateIntegrationRequest createIntegrationRequest)

Create new integration

Create a new third-party service integration for a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createIntegrationRequest** | [**CreateIntegrationRequest**](CreateIntegrationRequest.md) |  |  |

### Return type

[**CreateIntegration201Response**](CreateIntegration201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Integration created |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deleteintegration"></a>
# **DeleteIntegration**
> MessageResponse DeleteIntegration (string projectId, string integrationId)

Delete integration

Delete an integration from a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration deleted |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="executeintegration"></a>
# **ExecuteIntegration**
> TestWalletWebhook200Response ExecuteIntegration (string projectId, string integrationId, ExecuteIntegrationRequest executeIntegrationRequest)

Execute integration

Execute an integration action (API call) with specified endpoint and parameters. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |
| **executeIntegrationRequest** | [**ExecuteIntegrationRequest**](ExecuteIntegrationRequest.md) |  |  |

### Return type

[**TestWalletWebhook200Response**](TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration executed |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="exportintegration"></a>
# **ExportIntegration**
> CreateIntegration201Response ExportIntegration (string projectId, string integrationId)

Export integration

Export integration configuration for backup or migration. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |

### Return type

[**CreateIntegration201Response**](CreateIntegration201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration export data |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getintegration"></a>
# **GetIntegration**
> GetIntegration200Response GetIntegration (string projectId, string integrationId)

Get integration details

Get details of a specific integration. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |

### Return type

[**GetIntegration200Response**](GetIntegration200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getintegrations"></a>
# **GetIntegrations**
> GetIntegrations200Response GetIntegrations (string projectId)

Get project integrations

List all integrations configured for a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetIntegrations200Response**](GetIntegrations200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integrations list |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="gettemplates"></a>
# **GetTemplates**
> GetTemplates200Response GetTemplates ()

Get integration templates

Get available integration templates for third-party service connections. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetTemplates200Response**](GetTemplates200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration templates list |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getusagestats"></a>
# **GetUsageStats**
> GetUsageStats200Response GetUsageStats (string projectId, string integrationId, string period = null)

Get integration usage statistics

Get usage statistics for an integration (total calls, success/failure rates). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |
| **period** | **string** |  | [optional] [default to month] |

### Return type

[**GetUsageStats200Response**](GetUsageStats200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage statistics |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="importintegration"></a>
# **ImportIntegration**
> CreateIntegration201Response ImportIntegration (string projectId, ImportIntegrationRequest importIntegrationRequest)

Import integration

Import an integration configuration from exported data. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **importIntegrationRequest** | [**ImportIntegrationRequest**](ImportIntegrationRequest.md) |  |  |

### Return type

[**CreateIntegration201Response**](CreateIntegration201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Integration imported |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="testintegration"></a>
# **TestIntegration**
> TestWalletWebhook200Response TestIntegration (string projectId, string integrationId, TestIntegrationRequest testIntegrationRequest)

Test integration

Test an integration connection and configuration. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |
| **testIntegrationRequest** | [**TestIntegrationRequest**](TestIntegrationRequest.md) |  |  |

### Return type

[**TestWalletWebhook200Response**](TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration test result |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updateintegration"></a>
# **UpdateIntegration**
> CreateIntegration201Response UpdateIntegration (string projectId, string integrationId, UpdateIntegrationRequest updateIntegrationRequest)

Update integration

Update integration configuration (name, config, credentials). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **integrationId** | **string** |  |  |
| **updateIntegrationRequest** | [**UpdateIntegrationRequest**](UpdateIntegrationRequest.md) |  |  |

### Return type

[**CreateIntegration201Response**](CreateIntegration201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Integration updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

