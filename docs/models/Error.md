# Mudbase.SDK.Model.Error
API error payload. The backend returns an **error** string (required); **code**, **details**, **timestamp**, **path**, and **requestId** are optional. The **error** message is exactly as returned by the backend and varies by endpoint (e.g. \"File not found\", \"Project not found\", \"Invalid token.\"). 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**VarError** | **string** | Exact error message from the backend | 
**Code** | **string** |  | [optional] 
**Details** | [**ErrorDetails**](ErrorDetails.md) |  | [optional] 
**Timestamp** | **DateTime** |  | [optional] 
**Path** | **string** |  | [optional] 
**RequestId** | **string** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

