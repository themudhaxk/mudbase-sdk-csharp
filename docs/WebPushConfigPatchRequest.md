# Mudbase.SDK.Model.WebPushConfigPatchRequest
All fields optional. `enabled` toggles native Web Push (and provisions a keypair on first enable); `rotateKeys` regenerates the keypair (invalidating existing subscriptions); `subject` sets the RFC 8292 contact URI. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Enabled** | **bool** |  | [optional] 
**RotateKeys** | **bool** |  | [optional] 
**Subject** | **string** | A &#x60;mailto:&#x60; address or an &#x60;https&#x60; URL. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

