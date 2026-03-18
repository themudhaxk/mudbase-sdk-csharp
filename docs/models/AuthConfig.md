# Mudbase.SDK.Model.AuthConfig
Project auth configuration (providers, notifyOnNewSignIn).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Providers** | [**List&lt;AuthProvider&gt;**](AuthProvider.md) |  | [optional] 
**NotifyOnNewSignIn** | **bool** | When true, a \&quot;new sign-in detected\&quot; email is sent to the user on each app sign-in (local or OAuth). Counts against the org&#39;s messaging/email plan quota. Default false. Organization-based sign-in always sends this email (no quota deduction).  | [optional] [default to false]

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

