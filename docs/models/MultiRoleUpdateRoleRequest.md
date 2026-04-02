# Mudbase.SDK.Model.MultiRoleUpdateRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | [optional] 
**Description** | **string** |  | [optional] 
**SignupEndpoint** | **string** |  | [optional] 
**RequiresApproval** | **bool** |  | [optional] 
**RequiresPayment** | **bool** |  | [optional] 
**RequiresKYC** | **bool** |  | [optional] 
**DefaultPermissions** | **List&lt;Object&gt;** |  | [optional] 
**CollectionPermissions** | [**Dictionary&lt;string, AppRoleCollectionPermissionValue&gt;**](AppRoleCollectionPermissionValue.md) | Per-collection CRUD map (same as POST add role). | [optional] 
**Metadata** | **Object** |  | [optional] 
**FeaturePermissions** | **Dictionary&lt;string, Dictionary&lt;string, bool&gt;&gt;** | Per-role feature toggles for app JWTs: &#x60;{ [resource]: { [action]: boolean } }&#x60;. Use resource and action names that match the public API contract (see multi-role guide and simulate-permissions). **Messaging** accepts legacy keys (&#x60;email&#x60;, &#x60;sms&#x60;, &#x60;push&#x60;, …) and newer names (&#x60;send_email&#x60;, &#x60;send_sms&#x60;, …) as synonyms. Common resources: &#x60;messaging&#x60;, &#x60;integration&#x60;, &#x60;functions&#x60;, &#x60;data&#x60;, &#x60;search&#x60;, &#x60;usage&#x60;, &#x60;storage&#x60;, &#x60;chat&#x60;, &#x60;realtime&#x60;, &#x60;roleElevation&#x60;, &#x60;webhooks&#x60;.  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

