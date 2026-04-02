# Mudbase.SDK.Model.ChatSendMessageRequestE2ee
Opaque end-to-end encrypted payload (base64 ciphertext). Server cannot decrypt. Only for type=text.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**VarVersion** | **int** |  | [optional] [default to 1]
**Scheme** | **string** |  | [optional] 
**Ciphertext** | **string** | Base64-encoded ciphertext. | [optional] 
**Nonce** | **string** |  | [optional] 
**EphemeralPublicKey** | **string** |  | [optional] 
**SenderKeyId** | **string** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

