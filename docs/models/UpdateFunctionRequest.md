# Mudbase.SDK.Model.UpdateFunctionRequest
Fields to update on a function (name, description, code, trigger, environment, isActive, limits, retryPolicy).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | [optional] 
**Description** | **string** |  | [optional] 
**Code** | **string** |  | [optional] 
**Trigger** | [**FunctionTrigger**](FunctionTrigger.md) |  | [optional] 
**VarEnvironment** | **Object** |  | [optional] 
**IsActive** | **bool** |  | [optional] 
**Limits** | [**UpdateFunctionRequestLimits**](UpdateFunctionRequestLimits.md) |  | [optional] 
**RetryPolicy** | [**UpdateFunctionRequestRetryPolicy**](UpdateFunctionRequestRetryPolicy.md) |  | [optional] 
**VersionComment** | **string** | Comment for version when code is updated | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

