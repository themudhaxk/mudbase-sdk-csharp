# Mudbase.SDK.Model.InitializeOrgPlanCheckoutRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**PlanName** | **string** | Plan id from GET /api/billing/plans (excludes free and enterprise) | 
**BillingCycle** | **string** | Yearly &#x3D; 8% discount | [optional] [default to BillingCycleEnum.Monthly]
**RedirectUrl** | **string** | Override redirect after payment (default FRONTEND_URL/billing/callback) | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

