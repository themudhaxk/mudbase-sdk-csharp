# Mudbase.SDK.Model.PushSentResponse
Result of a push send, summarized per channel. `channels.fcm` covers the device-token channel and `channels.webPush` the native Web Push channel; each is `null` when that channel had no targets in the request. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Success** | **bool** |  | [optional] 
**Data** | [**PushSentResponseData**](PushSentResponseData.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

