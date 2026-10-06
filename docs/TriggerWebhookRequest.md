# Mudbase.SDK.Model.TriggerWebhookRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**ProjectId** | **string** | Target project (must belong to your org) | 
**Url** | **string** | HTTPS URL validated against SSRF rules | 
**Event** | **string** | Event name (sent as X-MUDBASE-Event) | 
**Payload** | **Object** | JSON body POSTed to your endpoint | 
**Method** | **string** |  | [optional] [default to MethodEnum.POST]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

