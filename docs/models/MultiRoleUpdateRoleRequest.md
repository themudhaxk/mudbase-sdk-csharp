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
**CollectionPermissions** | [**Dictionary&lt;string, MultiRoleUpdateRoleRequestCollectionPermissionsValue&gt;**](MultiRoleUpdateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map (same as POST add role). | [optional] 
**Metadata** | **Object** |  | [optional] 
**FeaturePermissions** | **Dictionary&lt;string, Dictionary&lt;string, bool&gt;&gt;** | App JWT feature toggles on &#x60;MultiRoleFeature.roles[].featurePermissions&#x60;: &#x60;{ [resource]: { [action]: boolean } }&#x60;. Canonical &#x60;(resource, action)&#x60; pairs: &#x60;services/appRoleFeatureMap.js&#x60;. Inventory: &#x60;node scripts/verify-app-role-feature-map.js&#x60;. Messaging accepts legacy keys (&#x60;email&#x60;, &#x60;sms&#x60;, …) and newer names (&#x60;send_email&#x60;, …) per &#x60;appRoleFeatureService.js&#x60;. Resources: messaging, integration, functions, data, search, usage, storage, chat, realtime, roleElevation, webhooks — see table in &#x60;openapi.yaml&#x60; component &#x60;AppRoleFeaturePermissions&#x60;.  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

