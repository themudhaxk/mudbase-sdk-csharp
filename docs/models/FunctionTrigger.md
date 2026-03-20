# Mudbase.SDK.Model.FunctionTrigger
Function trigger config (type, event, schedule, path, method, collectionId, bucketId).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Type** | **string** | Trigger type | 
**Event** | **string** | Event name (e.g. create, update, delete for document; uploaded, deleted for file; tx, balance for wallet) | [optional] 
**Schedule** | **string** | For cron - minutely, hourly, daily, weekly, or custom cron expression | [optional] 
**Path** | **string** | HTTP path for http triggers | [optional] 
**Method** | **string** |  | [optional] 
**CollectionId** | **string** | For document triggers - filter by collection | [optional] 
**BucketId** | **string** | For file triggers - filter by bucket | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

