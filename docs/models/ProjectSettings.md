# Mudbase.SDK.Model.ProjectSettings
Project-level settings. Toggles for verification and default user status apply to app and role-based signup. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AllowAnonymousAuth** | **bool** | Allow anonymous (unauthenticated) users | [optional] [default to true]
**RequireEmailVerification** | **bool** | When true, users who sign up with email do not receive a token until they verify their email; login is blocked until verified. | [optional] [default to true]
**RequirePhoneVerification** | **bool** | When true, users who sign in with phone (e.g. OTP) must have verified their phone before receiving a token. | [optional] [default to false]
**DefaultUserAccountStatus** | **string** | Default account status for new signups. **active** &#x3D; user can use the app immediately. **pending** &#x3D; user must be approved by an org owner/admin (PATCH org user status to active) before they can perform protected operations.  | [optional] [default to DefaultUserAccountStatusEnum.Active]
**EnableRealtime** | **bool** |  | [optional] [default to true]
**EnableStorage** | **bool** |  | [optional] [default to true]
**EnableFunctions** | **bool** |  | [optional] [default to false]

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

