# Mudbase.SDK.Model.DashboardOverviewDataLatency
Per-project weighted mean latency from UsageStat for routes in openapi-docs.yaml (customer/project API only).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Scope** | **string** |  | [optional] 
**AvgMsToday** | **int** |  | [optional] 
**AvgMs7d** | **int** |  | [optional] 
**LatencySamplesToday** | **int** | Count of openapi-docs–scoped latency samples for this project (UTC today) | [optional] 
**LatencyNeedsTraffic** | **bool** |  | [optional] 
**Interpretation** | **string** | Why mean can differ from typical latency; points to latency-insights | [optional] 
**InstanceRollup** | [**DashboardOverviewDataLatencyInstanceRollup**](DashboardOverviewDataLatencyInstanceRollup.md) |  | [optional] 
**TopRoutesByImpactHint** | [**List&lt;DashboardOverviewDataLatencyTopRoutesByImpactHintInner&gt;**](DashboardOverviewDataLatencyTopRoutesByImpactHintInner.md) | Top route templates by impact score on this instance (debugging hint) | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

