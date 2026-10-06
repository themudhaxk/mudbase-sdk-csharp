# Mudbase.SDK.Model.PushSentResponseData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Success** | **bool** | True when at least one recipient across any channel was delivered to. | [optional] 
**MessageId** | **string** |  | [optional] 
**SuccessCount** | **int** |  | [optional] 
**FailureCount** | **int** |  | [optional] 
**Channels** | [**PushSentResponseDataChannels**](PushSentResponseDataChannels.md) |  | [optional] 
**RejectedTokens** | **List&lt;string&gt;** | Device tokens that were passed but are not registered to the project, and so were dropped. Omitted when empty.  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

