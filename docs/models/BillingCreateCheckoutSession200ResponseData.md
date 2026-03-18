# Mudbase.SDK.Model.BillingCreateCheckoutSession200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**CheckoutUrl** | **string** | Checkout/page URL (crypto) or null when Flutterwave | [optional] 
**AuthorizationUrl** | **string** | Flutterwave redirect URL (when Flutterwave is used) | [optional] 
**AccessCode** | **string** | Flutterwave access code | [optional] 
**Reference** | **string** | Payment reference (e.g. mudbase_xxx or pmt_xxx) | [optional] 
**PaymentId** | **string** | Payment intent ID (crypto) | [optional] 
**PaymentOptions** | [**List&lt;BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner&gt;**](BillingCreateCheckoutSession200ResponseDataPaymentOptionsInner.md) | Multi-chain payment options (crypto) | [optional] 
**PaymentAddress** | **string** |  | [optional] 
**Network** | **string** |  | [optional] 
**Asset** | **string** |  | [optional] 
**Amount** | **decimal** |  | [optional] 
**Currency** | **string** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

