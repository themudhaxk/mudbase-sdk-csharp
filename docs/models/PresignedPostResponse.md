# Mudbase.SDK.Model.PresignedPostResponse
Presigned POST data for direct upload (key, url, fields, expiresIn).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Key** | **string** | Object key (S3) clients should upload to | [optional] 
**Url** | **string** | URL to POST the multipart form to | [optional] 
**Fields** | **Object** | Form fields required for the presigned POST (Policy, X-Amz-Signature, etc.) | [optional] 
**ExpiresIn** | **int** | Expiration of the presigned POST in seconds | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

