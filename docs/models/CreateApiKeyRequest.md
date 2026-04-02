# Mudbase.SDK.Model.CreateApiKeyRequest
Payload to create an API key (name, projectId, permissions, rateLimit, expiresAt).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | 
**ProjectId** | **string** | MongoDB ObjectId of the project | 
**Permissions** | [**List&lt;ApiKeyPermission&gt;**](ApiKeyPermission.md) | Optional. Permission objects (resource + actions). Omit or pass [] for full access (all resources and actions). Include only the entries you want; remove resources or actions to restrict the key. | [optional] 
**RateLimit** | [**RateLimit**](RateLimit.md) |  | [optional] 
**ExpiresAt** | **DateTime** | Optional. When provided, must be a valid ISO 8601 date-time in the future. Omit for no expiration. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

