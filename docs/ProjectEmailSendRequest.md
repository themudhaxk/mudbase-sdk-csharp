# Mudbase.SDK.Model.ProjectEmailSendRequest
Either `template` (with optional `data`) or both `subject` and `html` must be provided. `to` may be a string or array of strings. For named templates, **`data`** should supply values for `{{placeholders}}` (see **Email** tag description for the full list). 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Template** | **string** | Registered template name resolved by the email worker | [optional] 
**To** | [**EmailRequestTo**](EmailRequestTo.md) |  | [optional] 
**Data** | **Dictionary&lt;string, Object&gt;** |  | [optional] 
**Subject** | **string** |  | [optional] 
**Html** | **string** |  | [optional] 
**IdempotencyKey** | **string** |  | [optional] 
**BrandingScope** | **string** | Email layout branding; defaults from project context when omitted | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

