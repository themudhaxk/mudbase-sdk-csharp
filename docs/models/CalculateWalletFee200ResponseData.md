# Mudbase.SDK.Model.CalculateWalletFee200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Currency** | **string** | Request currency / native currency for the chain | [optional] 
**Network** | **string** |  | [optional] 
**Amount** | **decimal** |  | [optional] 
**Chain** | **string** | Chain id used for estimation | [optional] 
**NetworkFee** | **string** | Human-readable network fee from blockchain | [optional] 
**EstimatedTime** | **string** |  | [optional] 
**Congestion** | **string** | Network congestion level (EVM from gas price; UTXO from sat/vB) | [optional] 
**GasLimit** | **string** | (EVM only) Gas limit | [optional] 
**GasPrice** | **string** | (EVM only) Gas price in wei | [optional] 
**GasPriceGwei** | **decimal** | (EVM only) Gas price in Gwei | [optional] 
**EstimatedCost** | **string** | (EVM only) Cost in wei | [optional] 
**SatPerVb** | **int** | (UTXO only) Satoshis per vbyte | [optional] 
**FeeSat** | **int** | (UTXO only) Fee in satoshis | [optional] 
**Lamports** | **int** | (Solana only) Fee in lamports | [optional] 
**FeeTiers** | [**Dictionary&lt;string, CalculateWalletFee200ResponseDataFeeTiersValue&gt;**](CalculateWalletFee200ResponseDataFeeTiersValue.md) | (EVM only) slow / normal / fast tiers; each has gasPriceGwei, networkFee | [optional] 
**GasSpikeWarning** | **bool** | True when current gas is ≥5× chain minimum (consider warning user) | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

