# Mudbase.SDK.Model.PaymentSubscription
Subscription record (id, plan, status, currentPeriodEnd, etc.).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**Merchant** | **string** | Merchant ID | [optional] 
**Project** | **string** | Project ID | [optional] 
**Amount** | **decimal** | Subscription amount | [optional] 
**Interval** | **string** |  | [optional] 
**Network** | **string** |  | [optional] 
**Token** | **string** |  | [optional] 
**Status** | **string** |  | [optional] 
**NextPaymentAt** | **DateTime** | Next payment due date | [optional] 
**GracePeriodDays** | **int** | Grace period in days | [optional] [default to 3]
**EarlyPaymentAllowed** | **bool** |  | [optional] [default to true]
**LatePaymentAllowed** | **bool** |  | [optional] [default to true]
**ProrationEnabled** | **bool** |  | [optional] [default to false]
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

