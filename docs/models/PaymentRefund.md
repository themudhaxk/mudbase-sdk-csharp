# Mudbase.SDK.Model.PaymentRefund
Payment refund record (id, paymentId, amount, status, reason, createdAt).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**PaymentIntent** | **string** | Payment intent ID | [optional] 
**Merchant** | **string** | Merchant ID | [optional] 
**Amount** | **decimal** | Refund amount | [optional] 
**Reason** | **string** | Refund reason | [optional] 
**Status** | **string** |  | [optional] 
**IsCrossChain** | **bool** | True if cross-chain refund | [optional] [default to false]
**SourceNetwork** | **string** | Source network for refund | [optional] 
**TargetNetwork** | **string** | Target network for cross-chain refund | [optional] 
**ApprovedBy** | **string** | User ID who approved | [optional] 
**ApprovedAt** | **DateTime** |  | [optional] 
**RefundTx** | **string** | Refund transaction hash | [optional] 
**RefundedAt** | **DateTime** |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

