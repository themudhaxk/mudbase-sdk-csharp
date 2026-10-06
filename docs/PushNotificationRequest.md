# Mudbase.SDK.Model.PushNotificationRequest
Provide at least one target: `tokens` (registered device tokens), `endpoints` (registered Web Push subscription endpoints), `userIds` (Web Push subscriptions associated to those user ids), or `webPushBroadcast: true` (every enabled Web Push subscription in the project). A single send can target both the device-token channel and the native Web Push channel at once. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Tokens** | **List&lt;string&gt;** | Registered device push tokens to deliver to (device-token channel). | [optional] 
**Endpoints** | **List&lt;string&gt;** | Registered Web Push subscription endpoints to deliver to (native Web Push channel).  | [optional] 
**UserIds** | **List&lt;string&gt;** | Deliver to every Web Push subscription registered under these user ids (native Web Push channel).  | [optional] 
**WebPushBroadcast** | **bool** | When true, deliver to every enabled Web Push subscription registered to the project (native Web Push channel). Ignored when the project has not enabled native Web Push.  | [optional] 
**Title** | **string** |  | 
**Body** | **string** |  | 
**Data** | **Object** |  | [optional] 
**ImageUrl** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

