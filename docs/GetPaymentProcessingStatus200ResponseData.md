# Mudbase.SDK.Model.GetPaymentProcessingStatus200ResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Onboarded** | **bool** |  | [optional] 
**Enabled** | **bool** | Whether payment collection is actually toggled on (implies approved). | [optional] 
**ApprovalStatus** | **string** | not_submitted, pending_review, approved, or rejected. | [optional] 
**Status** | **string** | Derived overall status for the console to render: not_onboarded, pending_review, rejected, disabled, or active. | [optional] 
**RejectionReason** | **string** |  | [optional] 
**Stablecoin** | [**GetPaymentProcessingStatus200ResponseDataStablecoin**](GetPaymentProcessingStatus200ResponseDataStablecoin.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

