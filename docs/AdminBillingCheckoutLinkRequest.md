# Mudbase.SDK.Model.AdminBillingCheckoutLinkRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Plan** | **string** |  | 
**BillingCycle** | **string** |  | [optional] [default to BillingCycleEnum.Monthly]
**AmountCents** | **int** | Monthly amount in cents (overrides catalog; enterprise default is contract) | [optional] 
**ChargeAmountCents** | **int** | Exact charge in cents for this checkout (overrides monthly math) | [optional] 
**Currency** | **string** |  | [optional] 
**Email** | **string** |  | [optional] 
**Name** | **string** |  | [optional] 
**RedirectUrl** | **string** |  | [optional] 
**SendEmail** | **bool** |  | [optional] [default to false]
**ToEmail** | **string** |  | [optional] 
**Message** | **string** | Optional note shown in org_billing_checkout email | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

