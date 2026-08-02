# Mudbase.SDK.Model.CreateRoleRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | 
**Description** | **string** |  | [optional] 
**Permissions** | [**List&lt;CreateRoleRequestPermissionsInner&gt;**](CreateRoleRequestPermissionsInner.md) | Legacy resource-level permissions. For data CRUD, prefer &#x60;collectionPermissions&#x60; below. | [optional] 
**Hierarchy** | **decimal** |  | [optional] 
**CollectionPermissions** | [**Dictionary&lt;string, CreateRoleRequestCollectionPermissionsValue&gt;**](CreateRoleRequestCollectionPermissionsValue.md) | Per-collection CRUD map. Keys are collection slugs; value can be action array or object with actions + conditions. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

