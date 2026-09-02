# Mudbase.SDK.Model.DashboardOverviewDataUptime
Organization-wide uptime KPI; platformProbe* is infra (Mongo); projectHttp* is this project only for comparison.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Scope** | **string** |  | [optional] 
**DisplayPct30d** | **decimal?** |  | [optional] 
**DisplaySource** | **string** |  | [optional] 
**IsPreliminary** | **bool** |  | [optional] 
**PlatformProbePct30d** | **decimal?** |  | [optional] 
**PlatformSamples** | **int** |  | [optional] 
**PlatformOkSamples** | **int** |  | [optional] 
**OrgHttpNon5xxPct30d** | **decimal?** |  | [optional] 
**OrgHttpSampled30d** | **int** |  | [optional] 
**OrgHttp5xx30d** | **int** | Metered 5xx count from UsageStat (trackApiCall) | [optional] 
**ProjectHttp5xx30d** | **int** | This project’s metered 5xx count (30d) | [optional] 
**GlobalHttpNon5xxPct30d** | **decimal?** | Deprecated alias for orgHttpNon5xxPct30d | [optional] 
**GlobalHttpSampled30d** | **int** | Deprecated alias for orgHttpSampled30d | [optional] 
**RequestNon5xxPct30d** | **decimal?** | Deprecated alias for orgHttpNon5xxPct30d | [optional] 
**RequestSampled30d** | **int** | Deprecated alias for orgHttpSampled30d | [optional] 
**ProjectHttpNon5xxPct30d** | **decimal?** |  | [optional] 
**ProjectHttpSampled30d** | **int** |  | [optional] 
**Help** | **string** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

