# Mudbase.SDK.Model.GetPayoutCountries200ResponseDataCountriesInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Code** | **string** | ISO-3166 alpha-2 country code (e.g. NG, GH, KE, US, GB). | [optional] 
**Name** | **string** |  | [optional] 
**Currency** | **string** |  | [optional] 
**BanksListSupported** | **bool** | Whether GET /payment-processing/banks returns a live bank list for this country. | [optional] 
**MobileMoney** | **bool** |  | [optional] 
**International** | **bool** | True for a market whose settlement rail requires an account-level capability beyond the standard local-rail onboarding (currently US, GB). | [optional] 
**Fields** | [**List&lt;GetPayoutCountries200ResponseDataCountriesInnerFieldsInner&gt;**](GetPayoutCountries200ResponseDataCountriesInnerFieldsInner.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

