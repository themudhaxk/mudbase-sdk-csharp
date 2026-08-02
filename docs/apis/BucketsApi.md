# Mudbase.SDK.Api.BucketsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateBucket**](BucketsApi.md#createbucket) | **POST** /api/bucket/projects/{projectId}/buckets | Create a new bucket |
| [**DeleteBucket**](BucketsApi.md#deletebucket) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId} | Delete bucket |
| [**GetBucket**](BucketsApi.md#getbucket) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId} | Get bucket details |
| [**ListBuckets**](BucketsApi.md#listbuckets) | **GET** /api/bucket/projects/{projectId}/buckets | List buckets in a project |
| [**UpdateBucket**](BucketsApi.md#updatebucket) | **PATCH** /api/bucket/projects/{projectId}/buckets/{bucketId} | Update bucket |

<a id="createbucket"></a>
# **CreateBucket**
> BucketResponse CreateBucket (string projectId, CreateBucketRequest createBucketRequest)

Create a new bucket

Create a new storage bucket in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createBucketRequest** | [**CreateBucketRequest**](CreateBucketRequest.md) |  |  |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Bucket created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletebucket"></a>
# **DeleteBucket**
> MessageResponse DeleteBucket (string projectId, string bucketId)

Delete bucket

Delete a storage bucket permanently. This is a destructive operation that will also delete all files in the bucket. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |

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
| **200** | Bucket deleted successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getbucket"></a>
# **GetBucket**
> BucketResponse GetBucket (string projectId, string bucketId)

Get bucket details


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bucket details |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listbuckets"></a>
# **ListBuckets**
> BucketListResponse ListBuckets (string projectId, int page = null, int limit = null, string search = null)

List buckets in a project

List all storage buckets in a project with pagination and search. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |
| **search** | **string** |  | [optional]  |

### Return type

[**BucketListResponse**](BucketListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of buckets |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatebucket"></a>
# **UpdateBucket**
> BucketResponse UpdateBucket (string projectId, string bucketId, UpdateBucketRequest updateBucketRequest)

Update bucket

Update bucket configuration (name, public/private status, settings). Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **updateBucketRequest** | [**UpdateBucketRequest**](UpdateBucketRequest.md) |  |  |

### Return type

[**BucketResponse**](BucketResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Bucket updated successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

