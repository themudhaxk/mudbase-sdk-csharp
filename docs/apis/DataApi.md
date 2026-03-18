# Mudbase.SDK.Api.DataApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**DataCreate**](DataApi.md#datacreate) | **POST** /api/data/projects/{projectId}/collections/{collectionId}/data | Create data in collection |
| [**DataDelete**](DataApi.md#datadelete) | **DELETE** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Delete document |
| [**DataGet**](DataApi.md#dataget) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Get single document |
| [**DataList**](DataApi.md#datalist) | **GET** /api/data/projects/{projectId}/collections/{collectionId}/data | List data in collection |
| [**DataUpdate**](DataApi.md#dataupdate) | **PATCH** /api/data/projects/{projectId}/collections/{collectionId}/data/{documentId} | Update document |

<a id="datacreate"></a>
# **DataCreate**
> DataResponse DataCreate (string projectId, string collectionId, Object body)

Create data in collection

Create a new document in a collection. Request body must match the collection schema. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **collectionId** | **string** | Collection ID. |  |
| **body** | **Object** | Document fields matching the collection schema. |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Data created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="datadelete"></a>
# **DataDelete**
> MessageResponse DataDelete (string projectId, string collectionId, string documentId)

Delete document

Delete a document from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **collectionId** | **string** | Collection ID. |  |
| **documentId** | **string** | Document ID. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="dataget"></a>
# **DataGet**
> DataResponse DataGet (string projectId, string collectionId, string documentId)

Get single document

Get a document by ID from a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **collectionId** | **string** | Collection ID. |  |
| **documentId** | **string** | Document ID. |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Document data |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="datalist"></a>
# **DataList**
> DataListResponse DataList (string projectId, string collectionId, int page = null, int limit = null, string sort = null, string filter = null)

List data in collection

List all documents in a collection with optional pagination, sort, and filter. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **collectionId** | **string** | Collection ID. |  |
| **page** | **int** | Page number (1-based). | [optional] [default to 1] |
| **limit** | **int** | Number of documents per page. | [optional] [default to 20] |
| **sort** | **string** | Sort field and order (e.g. -createdAt, name). | [optional] [default to &quot;-createdAt&quot;] |
| **filter** | **string** | JSON string for filtering documents (e.g. {\&quot;status\&quot;:\&quot;active\&quot;}). | [optional]  |

### Return type

[**DataListResponse**](DataListResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="dataupdate"></a>
# **DataUpdate**
> DataResponse DataUpdate (string projectId, string collectionId, string documentId, Object body)

Update document

Update a document in a collection. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **collectionId** | **string** | Collection ID. |  |
| **documentId** | **string** | Document ID. |  |
| **body** | **Object** | Partial document fields to update. |  |

### Return type

[**DataResponse**](DataResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

