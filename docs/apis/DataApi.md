# Mudbase.SDK.Api.DataApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateData**](DataApi.md#createdata) | **POST** /api/data/projects/{projectId}/collections/{collectionId}/data | Create data in collection |
| [**DeleteData**](DataApi.md#deletedata) | **DELETE** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Delete document |
| [**GetData**](DataApi.md#getdata) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Get single document |
| [**ListData**](DataApi.md#listdata) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data | List data in collection |
| [**UpdateData**](DataApi.md#updatedata) | **PATCH** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Update document |

<a id="createdata"></a>
# **CreateData**
> DataResponse CreateData (string projectId, string collectionId, Object body)

Create data in collection


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **collectionId** | **string** |  |  |
| **body** | **Object** |  |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Data created |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletedata"></a>
# **DeleteData**
> MessageResponse DeleteData (string projectId, string collectionId, string documentId)

Delete document

Delete a document from a collection. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **collectionId** | **string** |  |  |
| **documentId** | **string** |  |  |

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
| **200** | Data deleted |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getdata"></a>
# **GetData**
> DataResponse GetData (string projectId, string collectionId, string documentId)

Get single document


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **collectionId** | **string** |  |  |
| **documentId** | **string** |  |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Document data |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listdata"></a>
# **ListData**
> DataListResponse ListData (string projectId, string collectionId, int page = null, int limit = null, string sort = null, string filter = null)

List data in collection

List all documents in a collection. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **collectionId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |
| **sort** | **string** |  | [optional] [default to &quot;-createdAt&quot;] |
| **filter** | **string** |  | [optional]  |

### Return type

[**DataListResponse**](DataListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data list |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatedata"></a>
# **UpdateData**
> DataResponse UpdateData (string projectId, string collectionId, string documentId, Object body)

Update document

Update a document in a collection. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **collectionId** | **string** |  |  |
| **documentId** | **string** |  |  |
| **body** | **Object** |  |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data updated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

