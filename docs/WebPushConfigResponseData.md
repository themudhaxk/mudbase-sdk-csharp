# Mudbase.SDK.Model.WebPushConfigResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Enabled** | **bool** | Whether native Web Push is enabled for this project. | [optional] 
**HasKeys** | **bool** | Whether a VAPID keypair has been provisioned. | [optional] 
**PublicKey** | **string** | The VAPID application-server public key clients subscribe with. Null when native Web Push is not enabled.  | [optional] 
**VapidSubject** | **string** | RFC 8292 contact subject (a &#x60;mailto:&#x60; address or &#x60;https&#x60; URL). | [optional] 
**GeneratedAt** | **DateTime?** | When the current VAPID keypair was generated. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

