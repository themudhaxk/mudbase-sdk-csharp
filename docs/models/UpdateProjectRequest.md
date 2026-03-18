# Mudbase.SDK.Model.UpdateProjectRequest
Fields to update on a project (name, description, logoUrl, settings, auth).

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Name** | **string** |  | [optional] 
**Description** | **string** |  | [optional] 
**LogoUrl** | **string** | Public URL for the project logo/brand image. Prefer uploading via **POST /api/projects/{id}/logo** or **POST /api/projects/{orgId}/projects/{id}/logo** (stored under logo/project/ in platform storage). Used in project-related emails.  | [optional] 
**Settings** | [**ProjectSettings**](ProjectSettings.md) |  | [optional] 
**Auth** | [**AuthConfig**](AuthConfig.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

