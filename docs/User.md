# Mudbase.SDK.Model.User

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**Email** | **string** |  | [optional] 
**FirstName** | **string** |  | [optional] 
**LastName** | **string** |  | [optional] 
**FullName** | **string** |  | [optional] 
**Avatar** | **string** |  | [optional] 
**Role** | **string** |  | [optional] 
**CustomRole** | **string** | Application-level role slug from the project&#39;s Multi-Role feature (e.g. \&quot;customer\&quot;, \&quot;seller\&quot;). Null for org-level (org/admin/member/viewer) users who aren&#39;t project end-users. | [optional] 
**IsAnonymous** | **bool** | True for a guest session created via POST /api/auth/anonymous that hasn&#39;t been converted to a full account yet. | [optional] 
**EmailVerified** | **bool** |  | [optional] 
**PhoneVerified** | **bool** |  | [optional] 
**TwoFactorEnabled** | **bool** |  | [optional] 
**LastLogin** | **DateTime** |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**UpdatedAt** | **DateTime** |  | [optional] 
**Org** | [**OrganizationSummary**](OrganizationSummary.md) |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

