# Mudbase.SDK.Model.ApiKey
API key entity (id, name, project, permissions, rateLimit, usage, isActive, expiresAt).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**Name** | **string** |  | [optional] 
**Project** | [**ProjectSummary**](ProjectSummary.md) |  | [optional] 
**Permissions** | [**List&lt;ApiKeyPermission&gt;**](ApiKeyPermission.md) |  | [optional] 
**RateLimit** | [**RateLimit**](RateLimit.md) |  | [optional] 
**Usage** | [**ApiKeyUsage**](ApiKeyUsage.md) |  | [optional] 
**IsActive** | **bool** |  | [optional] 
**ExpiresAt** | **DateTime** |  | [optional] 
**CreatedBy** | [**UserSummary**](UserSummary.md) |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

