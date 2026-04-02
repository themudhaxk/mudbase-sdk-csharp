# Mudbase.SDK.Model.AuthLogin200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Message** | **string** |  | [optional] 
**Token** | **string** | JWT access token (use in Authorization Bearer header) | [optional] 
**RefreshToken** | **string** | JWT refresh token (use with POST /api/auth/refresh to get new token pair) | [optional] 
**ExpiresIn** | **int** | Access token TTL in seconds (e.g. 1800 for 30 minutes) | [optional] 
**User** | [**AuthLogin200ResponseUser**](AuthLogin200ResponseUser.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

