# Mudbase.SDK.Model.SignedUrlResponse
Signed URL for temporary file access (url, expiresAt or expiresIn).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Success** | **bool** |  | [optional] 
**Url** | **string** | Signed URL for file access | [optional] 
**ExpiresAt** | **DateTime** | Expiration time of the signed URL (optional - some endpoints return expiresIn instead) | [optional] 
**ExpiresIn** | **int** | Time-to-live in seconds for the signed URL (optional) | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

