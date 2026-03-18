# Mudbase.SDK.Model.AuthRegister201Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Message** | **string** |  | [optional] 
**RequireVerification** | **bool** | true when email verification is required; no token in response | [optional] 
**Token** | **string** | Present only when requireEmailVerification is false | [optional] 
**RefreshToken** | **string** | Present only when requireEmailVerification is false | [optional] 
**ExpiresIn** | **int** | Present only when token is returned | [optional] 
**User** | [**AuthRegister201ResponseUser**](AuthRegister201ResponseUser.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

