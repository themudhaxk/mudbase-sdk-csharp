# Mudbase.SDK.Model.EmailTemplateCatalogItem
One row from GET /email/templates (full catalog for the project).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | [optional] 
**IsCustomized** | **bool** | True if this project has a stored override for this template name. | [optional] 
**EffectiveSource** | **string** | Which layer is used at send time for this name. | [optional] 
**SubjectSnippet** | **string** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 
**VarVersion** | **int** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

