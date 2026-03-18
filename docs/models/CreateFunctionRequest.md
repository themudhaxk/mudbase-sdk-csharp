# Mudbase.SDK.Model.CreateFunctionRequest
Payload to create a function (name, description, code, trigger, environment).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | 
**Code** | **string** | Function body (async, has access to payload, db, files, messaging, wallet, utils, env, console) | 
**Trigger** | [**FunctionTrigger**](FunctionTrigger.md) |  | 
**Description** | **string** |  | [optional] 
**VarEnvironment** | **Dictionary&lt;string, string&gt;** | Per-function env vars injected into sandbox | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

