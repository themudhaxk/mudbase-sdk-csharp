# Mudbase.SDK.Model.ConfigureWebhookRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**WebhookUrl** | **string** | URL to receive webhook payloads; set to null or omit to disable | [optional] 
**WebhookSecret** | **string** | Optional secret for signing payloads (e.g. X-Webhook-Signature) | [optional] 
**WebhookEvents** | **List&lt;string&gt;** | Event types to send (e.g. collection.insert, collection.update) | [optional] 
**WebhookVersion** | **string** | Version string for payload format | [optional] 
**Transformations** | [**List&lt;GetWebhookConfig200ResponseDataTransformationsInner&gt;**](GetWebhookConfig200ResponseDataTransformationsInner.md) | Transformation rules to apply to payloads before delivery | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

