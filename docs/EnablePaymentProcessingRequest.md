# Mudbase.SDK.Model.EnablePaymentProcessingRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Country** | **string** | ISO-3166 alpha-2 payout country code, one of the codes returned by GET /payment-processing/countries (e.g. NG, GH, KE, US, GB). | 
**BusinessName** | **string** |  | 
**BusinessMobile** | **string** | Optional, used for payout provider account notifications. | [optional] 
**AccountBank** | **string** | Bank code, mobile-money network code, routing number, or sort code, depending on country. | [optional] 
**AccountNumber** | **string** | Bank/mobile-money account number, IBAN, or similar, depending on country. | [optional] 
**Bvn** | **string** | Required only when country is NG (Nigeria). | [optional] 
**AccountType** | **string** | Required only when country is US (checking or savings). | [optional] 
**AccountHolderName** | **string** | Required only when country is US or GB. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

