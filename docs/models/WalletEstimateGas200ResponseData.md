# Mudbase.SDK.Model.WalletEstimateGas200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Chain** | **string** | Chain id (e.g. bsc, ethereum, bitcoin) | [optional] 
**GasLimit** | **string** | (EVM only) Estimated gas limit from RPC eth_estimateGas | [optional] 
**GasPrice** | **string** | (EVM only) Gas price in wei | [optional] 
**GasPriceGwei** | **decimal** | (EVM only) Gas price in Gwei | [optional] 
**EstimatedCost** | **string** | (EVM only) Total cost in wei (gasLimit * gasPrice) | [optional] 
**NetworkFee** | **string** | Human-readable network fee from blockchain (e.g. \&quot;0.00063 ETH\&quot;, \&quot;0.00001 BTC\&quot;) | [optional] 
**EstimatedTime** | **string** | Estimated confirmation time when available | [optional] 
**Currency** | **string** | Native currency for the chain (ETH, BNB, MATIC, BTC, SOL, TRX, etc.) | [optional] 
**SatPerVb** | **int** | (UTXO only) Satoshis per virtual byte | [optional] 
**FeeSat** | **int** | (UTXO only) Estimated fee in satoshis | [optional] 
**Lamports** | **int** | (Solana only) Fee in lamports | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

