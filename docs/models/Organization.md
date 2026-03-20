# Mudbase.SDK.Model.Organization
Organization (org) entity with plan, usage, limits, and billing.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**Name** | **string** |  | [optional] 
**Slug** | **string** |  | [optional] 
**Description** | **string** |  | [optional] 
**Logo** | **string** | Optional logo URL. Org-related emails use the platform logo (env); this field is for legacy or future UI use only. | [optional] 
**Website** | **string** |  | [optional] 
**Plan** | [**Plan**](Plan.md) |  | [optional] 
**Usage** | [**Usage**](Usage.md) |  | [optional] 
**Limits** | [**Limits**](Limits.md) |  | [optional] 
**Billing** | [**Billing**](Billing.md) |  | [optional] 
**Settings** | **Object** |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

