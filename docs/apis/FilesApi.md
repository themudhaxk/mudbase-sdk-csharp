# Mudbase.SDK.Api.FilesApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiFilesDownloadFileIdGet**](FilesApi.md#apifilesdownloadfileidget) | **GET** /api/files/download/{fileId} | Get a download URL for a file |
| [**ApiFilesLogoRedirectGet**](FilesApi.md#apifileslogoredirectget) | **GET** /api/files/logo-redirect | Redirect to an org/project logo&#39;s content |
| [**ApiFilesPublicFileIdGet**](FilesApi.md#apifilespublicfileidget) | **GET** /api/files/public/{fileId} | Redirect to a public file&#39;s content |
| [**ConfirmDirectUpload**](FilesApi.md#confirmdirectupload) | **POST** /api/files/upload/confirm | Confirm direct upload (scan + finalize metadata) |
| [**DeleteFile**](FilesApi.md#deletefile) | **DELETE** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Delete file |
| [**DownloadBucketFile**](FilesApi.md#downloadbucketfile) | **GET** /api/bucket/files/{fileId}/download | Download file from bucket |
| [**DownloadFile**](FilesApi.md#downloadfile) | **GET** /api/files/{fileId}/download | Generate a presigned URL for downloading a file |
| [**GeneratePresignedUpload**](FilesApi.md#generatepresignedupload) | **POST** /api/files/upload/presigned | Generate a presigned PUT URL for direct browser upload |
| [**GenerateSignedUrl**](FilesApi.md#generatesignedurl) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId}/signed-url | Generate signed URL for file |
| [**GetFile**](FilesApi.md#getfile) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files/{fileId} | Get file metadata |
| [**ListFiles**](FilesApi.md#listfiles) | **GET** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | List files in bucket |
| [**UploadFiles**](FilesApi.md#uploadfiles) | **POST** /api/bucket/projects/{projectId}/buckets/{bucketId}/files | Upload files to bucket |

<a id="apifilesdownloadfileidget"></a>
# **ApiFilesDownloadFileIdGet**
> ApiFilesDownloadFileIdGet200Response ApiFilesDownloadFileIdGet (string fileId, int expiresIn = null)

Get a download URL for a file

Returns a URL to download the file. For private files a short-lived signed URL is generated; the lifetime can be tuned per request via the optional expiresIn query parameter (seconds, clamped to a safe server-configured range). For public (public-read) files the permanent world-readable URL is returned with isPublic true and a warning, since signing a public object provides no protection. Accepts a JWT (Bearer) or a project API key.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **fileId** | **string** |  |  |
| **expiresIn** | **int** | Signed-URL lifetime in seconds for private files. Clamped to the server&#39;s min/max range; ignored for public files. Defaults to the server&#39;s configured expiry. | [optional]  |

### Return type

[**ApiFilesDownloadFileIdGet200Response**](ApiFilesDownloadFileIdGet200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Download URL (signed for private files, permanent for public files) |  -  |
| **403** | Access denied or download limit exceeded |  -  |
| **404** | File not found |  -  |
| **500** | Failed to generate download URL |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apifileslogoredirectget"></a>
# **ApiFilesLogoRedirectGet**
> void ApiFilesLogoRedirectGet (string key)

Redirect to an org/project logo's content

Unauthenticated. Logos are always meant to be public branding assets, but Cloudflare R2 has no per-object ACL, so this route (not the bucket) is what actually serves them - the `key` query param is validated against the exact shape logoStorageService.uploadLogo() produces before signing, so this can never be used to fetch an arbitrary storage key. 302-redirects to a short-lived signed GET url.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **key** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirect to a short-lived signed download URL |  -  |
| **400** | Key does not match the expected logo key shape |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apifilespublicfileidget"></a>
# **ApiFilesPublicFileIdGet**
> void ApiFilesPublicFileIdGet (string fileId)

Redirect to a public file's content

Unauthenticated. Only serves files with isPublic=true whose upload has been confirmed and whose virus scan came back clean - Cloudflare R2 has no per-object ACL, so this route (not the storage bucket) is what actually decides whether a \"public\" file's bytes are reachable. 302-redirects to a fresh, short-lived (60s) signed GET url so the actual bytes are still served straight off Cloudflare's edge.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **fileId** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirect to a short-lived signed download URL |  -  |
| **403** | File is not public |  -  |
| **404** | File not found, or not yet confirmed/scanned |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="confirmdirectupload"></a>
# **ConfirmDirectUpload**
> ConfirmUploadResponse ConfirmDirectUpload (ConfirmDirectUploadRequest confirmDirectUploadRequest)

Confirm direct upload (scan + finalize metadata)

After a client uploads directly to S3 using the presigned PUT URL, call this endpoint to have the server scan the object, create the File record, and optionally quarantine if infected.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **confirmDirectUploadRequest** | [**ConfirmDirectUploadRequest**](ConfirmDirectUploadRequest.md) |  |  |

### Return type

[**ConfirmUploadResponse**](ConfirmUploadResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | File confirmed and metadata stored |  -  |
| **400** | Bad request or file quarantined |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **413** | File or request body exceeds plan single-upload limit (or platform ceiling) |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletefile"></a>
# **DeleteFile**
> MessageResponse DeleteFile (string projectId, string bucketId, string fileId)

Delete file

Delete a file from a bucket permanently. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **fileId** | **string** |  |  |

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
| **200** | File deleted successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="downloadbucketfile"></a>
# **DownloadBucketFile**
> System.IO.Stream DownloadBucketFile (string fileId, string token = null)

Download file from bucket

Download a file from a bucket. For public files, no authentication is required. For private files, a download token (obtained via signed URL endpoint) is required in the query parameter. Accepts: Token-based authentication via query parameter (for private files), or no authentication (for public files). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **fileId** | **string** |  |  |
| **token** | **string** |  | [optional]  |

### Return type

**System.IO.Stream**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/octet-stream, application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | File download |  * Content-Type -  <br>  * Content-Length -  <br>  * Content-Disposition -  <br>  |
| **403** | Access denied or invalid token |  -  |
| **404** | File not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="downloadfile"></a>
# **DownloadFile**
> SignedUrlResponse DownloadFile (string fileId, string token = null)

Generate a presigned URL for downloading a file

Returns a time-limited provider-signed URL (S3) for direct download. Server enforces RBAC before issuing the URL.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **fileId** | **string** |  |  |
| **token** | **string** |  | [optional]  |

### Return type

[**SignedUrlResponse**](SignedUrlResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed URL generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="generatepresignedupload"></a>
# **GeneratePresignedUpload**
> PresignedPostResponse GeneratePresignedUpload (GeneratePresignedUploadRequest generatePresignedUploadRequest)

Generate a presigned PUT URL for direct browser upload

Issue a presigned PUT URL for clients to upload directly to object storage. The server stores the issued key with expiry and RBAC is enforced. PUT (not POST) is used because Cloudflare R2 does not implement the S3 POST Object API. The client must PUT the file body to `url` with the exact `headers` returned (a Content-Type mismatch fails with SignatureDoesNotMatch). `maxFileUploadBytes` is enforced server-side by `/api/files/upload/confirm` after the upload, not by the presigned URL itself. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **generatePresignedUploadRequest** | [**GeneratePresignedUploadRequest**](GeneratePresignedUploadRequest.md) |  |  |

### Return type

[**PresignedPostResponse**](PresignedPostResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Presigned PUT URL |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="generatesignedurl"></a>
# **GenerateSignedUrl**
> SignedUrlResponse GenerateSignedUrl (string projectId, string bucketId, string fileId, GenerateSignedUrlRequest generateSignedUrlRequest = null)

Generate signed URL for file

Generate a time-limited signed URL for downloading a private file. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **fileId** | **string** |  |  |
| **generateSignedUrlRequest** | [**GenerateSignedUrlRequest**](GenerateSignedUrlRequest.md) |  | [optional]  |

### Return type

[**SignedUrlResponse**](SignedUrlResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Signed URL generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfile"></a>
# **GetFile**
> FileResponse GetFile (string projectId, string bucketId, string fileId)

Get file metadata

Get metadata for a specific file in a bucket. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **fileId** | **string** |  |  |

### Return type

[**FileResponse**](FileResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | File metadata |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listfiles"></a>
# **ListFiles**
> FileListResponse ListFiles (string projectId, string bucketId, int page = null, int limit = null, string search = null, string type = null)

List files in bucket


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |
| **search** | **string** |  | [optional]  |
| **type** | **string** |  | [optional]  |

### Return type

[**FileListResponse**](FileListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of files |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="uploadfiles"></a>
# **UploadFiles**
> FileUploadResponse UploadFiles (string projectId, string bucketId, List<System.IO.Stream> files)

Upload files to bucket

Upload one or more files to a storage bucket using multipart/form-data. Per-file size is limited by the org plan (`maxFileUploadBytes`) and bucket `maxFileSize`, whichever is stricter. Exceeding the limit returns **413**. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **bucketId** | **string** |  |  |
| **files** | **List&lt;System.IO.Stream&gt;** |  |  |

### Return type

[**FileUploadResponse**](FileUploadResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: multipart/form-data
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Files uploaded successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **409** | Resource conflict |  -  |
| **413** | File or request body exceeds plan single-upload limit (or platform ceiling) |  -  |
| **429** | Rate limit exceeded |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

