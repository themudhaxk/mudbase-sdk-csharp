# Mudbase.SDK.Model.WebhookLog
One **outbound delivery attempt** (Mudbase HTTP client → your `url`). **`_id`** is what the API calls **`webhookId`** in **`POST /api/webhooks/trigger`** and **`POST /api/webhooks/retry/{webhookId}`**. The string field **`webhookId`** below is an internal correlation id (e.g. `manual-<timestamp>`), not the path parameter for retry. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** | MongoDB id — use as &#x60;webhookId&#x60; path param for retry | [optional] 
**Org** | **string** | Organization that owns the project | [optional] 
**Project** | **string** | Project id this delivery belongs to | [optional] 
**WebhookId** | **string** | Internal correlation string (e.g. manual-173…), not the retry path id | [optional] 
**Url** | **string** |  | [optional] 
**Method** | **string** |  | [optional] 
**Event** | **string** |  | [optional] 
**Status** | **string** |  | [optional] 
**Payload** | **Object** | JSON body sent to your endpoint | [optional] 
**Headers** | **Object** | Outbound request headers (e.g. X-MUDBASE-Event, Content-Type) | [optional] 
**Response** | [**WebhookLogResponse**](WebhookLogResponse.md) |  | [optional] 
**Duration** | **int** | Round-trip time in milliseconds | [optional] 
**Attempts** | **int** |  | [optional] 
**MaxAttempts** | **int** |  | [optional] 
**Error** | **string** |  | [optional] 
**NextRetry** | **DateTime** |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

