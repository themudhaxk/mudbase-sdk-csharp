# Mudbase.SDK.Model.UpdateCollectionPermissionsRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Actions** | **List&lt;UpdateCollectionPermissionsRequest.ActionsEnum&gt;** |  | [optional] 
**Conditions** | **Object** |  | [optional] 
**DataScope** | **string** | &#x60;all&#x60; &#x3D; no automatic row-owner filter. &#x60;own&#x60; &#x3D; only documents where the owner field matches the authenticated app user. | [optional] 
**OwnerField** | **string** | Optional override for the document field when dataScope is &#x60;own&#x60; (default &#x60;settings.dataOwnerField&#x60;, usually &#x60;createdBy&#x60;). | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

