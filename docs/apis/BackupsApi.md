# Mudbase.SDK.Api.BackupsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateBackup**](BackupsApi.md#createbackup) | **POST** /api/projects/{projectId}/backups | Create project backup |
| [**DeleteBackup**](BackupsApi.md#deletebackup) | **DELETE** /api/projects/{projectId}/backups/{backupId} | Delete backup |
| [**ListBackups**](BackupsApi.md#listbackups) | **GET** /api/projects/{projectId}/backups | List project backups |
| [**RestoreBackup**](BackupsApi.md#restorebackup) | **POST** /api/projects/{projectId}/backups/{backupId}/restore | Restore from backup |

<a id="createbackup"></a>
# **CreateBackup**
> CreateBackup201Response CreateBackup (string projectId, CreateBackupRequest createBackupRequest = null)

Create project backup

Create a backup of project data, optionally including files and wallets. Supports both JWT Bearer token and API key authentication.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createBackupRequest** | [**CreateBackupRequest**](CreateBackupRequest.md) |  | [optional]  |

### Return type

[**CreateBackup201Response**](CreateBackup201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Backup created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletebackup"></a>
# **DeleteBackup**
> DeleteBackup200Response DeleteBackup (string projectId, string backupId)

Delete backup

Delete a project backup. Supports both JWT Bearer token and API key authentication.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **backupId** | **string** |  |  |

### Return type

[**DeleteBackup200Response**](DeleteBackup200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Backup deleted successfully |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listbackups"></a>
# **ListBackups**
> ListBackups200Response ListBackups (string projectId)

List project backups

Get all backups for a project. Supports both JWT Bearer token and API key authentication.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**ListBackups200Response**](ListBackups200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of backups |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="restorebackup"></a>
# **RestoreBackup**
> RestoreBackup200Response RestoreBackup (string projectId, string backupId, RestoreBackupRequest restoreBackupRequest)

Restore from backup

Restore project data from a backup. Supports replace or merge modes. Supports both JWT Bearer token and API key authentication.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **backupId** | **string** |  |  |
| **restoreBackupRequest** | [**RestoreBackupRequest**](RestoreBackupRequest.md) |  |  |

### Return type

[**RestoreBackup200Response**](RestoreBackup200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Restore initiated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

