# Mudbase.SDK.Model.WebPushSubscription
A browser `PushSubscription` from `pushManager.subscribe()` - the push-service `endpoint` plus the `p256dh` / `auth` keys the server needs to encrypt a payload for that endpoint. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Endpoint** | **string** | The push-service endpoint URL returned by &#x60;pushManager.subscribe()&#x60;. | 
**Keys** | [**WebPushSubscriptionKeys**](WebPushSubscriptionKeys.md) |  | 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

