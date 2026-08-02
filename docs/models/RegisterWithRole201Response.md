# Mudbase.SDK.Model.RegisterWithRole201Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Message** | **string** |  | [optional] 
**RequireVerification** | **bool** | True when the project requires email verification before a session is issued - no token is returned in that case. | [optional] 
**Token** | **string** | JWT access token. Absent when requireVerification is true. | [optional] 
**RefreshToken** | **string** | JWT refresh token. Absent when requireVerification is true. | [optional] 
**ExpiresIn** | **int** | Access token TTL in seconds. Absent when requireVerification is true. | [optional] 
**User** | [**RegisterWithRole201ResponseUser**](RegisterWithRole201ResponseUser.md) |  | [optional] 
**Role** | [**RegisterWithRole201ResponseRole**](RegisterWithRole201ResponseRole.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

