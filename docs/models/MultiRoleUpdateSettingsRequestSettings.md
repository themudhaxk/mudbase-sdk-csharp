# Mudbase.SDK.Model.MultiRoleUpdateSettingsRequestSettings
Feature toggles for signup behavior (not per-role approval flags).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**AllowMultipleRoles** | **bool** | Whether an end user may hold multiple app roles. | [optional] 
**RequireRoleSelection** | **bool** | If true, signup must pick a role; if false and &#x60;autoAssignDefault&#x60; is true, &#x60;defaultRole&#x60; is used when omitted. | [optional] 
**AutoAssignDefault** | **bool** | When true, assigns &#x60;defaultRole&#x60; when the client does not specify a role at signup. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

