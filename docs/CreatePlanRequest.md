# Mudbase.SDK.Model.CreatePlanRequest
OpenAPI-style body normalized server-side into Plan.pricing (monthly/yearly amounts), features (objects with name/included), and optional limits/trial/metadata. Slug is derived from projectId + name unless a collision occurs. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** | Display name; also used to generate a unique slug per project. | 
**Description** | **string** |  | [optional] 
**Price** | **decimal** | Amount for the chosen interval. The server fills the other billing period (e.g. yearly ≈ monthly × 12 × 0.8 when interval is month).  | 
**Currency** | **string** | ISO currency code (stored lowercased). | 
**Interval** | **string** | Which period &#x60;price&#x60; applies to; drives pricing.monthly vs pricing.yearly. | 
**Features** | [**List&lt;CreatePlanRequestFeaturesInner&gt;**](CreatePlanRequestFeaturesInner.md) | Strings become &#x60;{ name, included: true }&#x60;. You may send full feature objects instead.  | [optional] 
**Limits** | [**CreatePlanRequestLimits**](CreatePlanRequestLimits.md) |  | [optional] 
**Trial** | [**CreatePlanRequestTrial**](CreatePlanRequestTrial.md) |  | [optional] 
**IsActive** | **bool** |  | [optional] [default to true]
**IsDefault** | **bool** | Only one default plan per project is allowed server-side. | [optional] [default to false]
**SortOrder** | **decimal** | Lower numbers list first in UIs. | [optional] 
**Metadata** | **Dictionary&lt;string, Object&gt;** | Arbitrary key/value data stored on the plan document. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

