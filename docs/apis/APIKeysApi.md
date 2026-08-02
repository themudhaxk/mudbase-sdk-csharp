# Mudbase.SDK.Api.APIKeysApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateApiKey**](APIKeysApi.md#createapikey) | **POST** /api/api-keys | Create API key |
| [**DeleteApiKey**](APIKeysApi.md#deleteapikey) | **DELETE** /api/api-keys/{id} | Delete API key |
| [**GetApiKeyUsage**](APIKeysApi.md#getapikeyusage) | **GET** /api/api-keys/{id}/usage | Get API key usage |
| [**ListApiKeys**](APIKeysApi.md#listapikeys) | **GET** /api/api-keys | List API keys |
| [**RegenerateApiKey**](APIKeysApi.md#regenerateapikey) | **POST** /api/api-keys/{id}/regenerate | Regenerate API key secret |
| [**UpdateApiKey**](APIKeysApi.md#updateapikey) | **PATCH** /api/api-keys/{id} | Update API key |

<a id="createapikey"></a>
# **CreateApiKey**
> CreateApiKey201Response CreateApiKey (CreateApiKeyRequest createApiKeyRequest)

Create API key

Create a new API key for a project with specified permissions. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createApiKeyRequest** | [**CreateApiKeyRequest**](CreateApiKeyRequest.md) |  |  |

### Return type

[**CreateApiKey201Response**](CreateApiKey201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | API key created |  -  |
| **400** | Validation failed (e.g. invalid permissions format, invalid or past expiresAt) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deleteapikey"></a>
# **DeleteApiKey**
> MessageResponse DeleteApiKey (string id)

Delete API key

Delete an API key. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | API key deleted |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getapikeyusage"></a>
# **GetApiKeyUsage**
> ApiKeyUsageResponse GetApiKeyUsage (string id)

Get API key usage

Get usage statistics for a specific API key including request count, rate limit status, and last used timestamp. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** |  |  |

### Return type

[**ApiKeyUsageResponse**](ApiKeyUsageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | API key usage statistics |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listapikeys"></a>
# **ListApiKeys**
> ListApiKeys200Response ListApiKeys ()

List API keys

List all API keys for the authenticated organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 


### Parameters
This endpoint does not need any parameter.
### Return type

[**ListApiKeys200Response**](ListApiKeys200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | API keys list |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="regenerateapikey"></a>
# **RegenerateApiKey**
> RegenerateApiKey200Response RegenerateApiKey (string id)

Regenerate API key secret

Regenerate the secret for an API key. The old secret will be invalidated immediately. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** |  |  |

### Return type

[**RegenerateApiKey200Response**](RegenerateApiKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | API key regenerated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updateapikey"></a>
# **UpdateApiKey**
> UpdateApiKey200Response UpdateApiKey (string id, UpdateApiKeyRequest updateApiKeyRequest)

Update API key

Update an API key's configuration (name, permissions, status). Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** |  |  |
| **updateApiKeyRequest** | [**UpdateApiKeyRequest**](UpdateApiKeyRequest.md) |  |  |

### Return type

[**UpdateApiKey200Response**](UpdateApiKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | API key updated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

