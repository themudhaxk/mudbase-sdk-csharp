# Mudbase.SDK.Model.Withdraw200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**TransactionId** | **string** |  | [optional] 
**Status** | **string** |  | [optional] 
**SignedTx** | **string** | Signed transaction (hex for EVM/UTXO, base64 for Solana, object for Tron). Send as-is in broadcast body. | [optional] 
**Chain** | **string** | Chain id for broadcast (e.g. ethereum, bitcoin, solana). | [optional] 
**FromAddress** | **string** | Sender address; must be registered for org when broadcasting. | [optional] 
**Currency** | **string** |  | [optional] 
**Amount** | **decimal** |  | [optional] 
**ToAddress** | **string** |  | [optional] 
**Message** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

