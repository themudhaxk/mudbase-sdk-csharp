# Mudbase.SDK.Model.PaymentIntent
Payment intent for checkout (id, amount, currency, status, etc.).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**PaymentId** | **string** | Unique payment identifier | [optional] 
**Merchant** | **string** | Merchant ID | [optional] 
**Project** | **string** | Project ID | [optional] 
**Amount** | **decimal** | Payment amount | [optional] 
**Currency** | **string** |  | [optional] [default to "USD"]
**Network** | **string** |  | [optional] 
**Token** | **string** |  | [optional] 
**Type** | **string** |  | [optional] 
**Status** | **string** |  | [optional] 
**FinalityStatus** | **string** |  | [optional] 
**TotalDue** | **decimal** | Total amount due including fees | [optional] 
**Commission** | **decimal** | Platform commission | [optional] 
**MerchantReceives** | **decimal** | Amount merchant receives after commission | [optional] 
**ExpiresAt** | **DateTime** |  | [optional] 
**Metadata** | **Object** | Additional metadata | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

