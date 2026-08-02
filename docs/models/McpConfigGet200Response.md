# Mudbase.SDK.Model.McpConfigGet200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Enabled** | **bool** |  | [optional] 
**Plan** | **string** |  | [optional] 
**AllowedPlans** | **List&lt;string&gt;** |  | [optional] 
**FreePromoActive** | **bool** | True if this org is on the free plan and MCP is temporarily enabled via the launch promo | [optional] 
**FreePromoEndsAt** | **DateTime** | When the free-plan MCP promo ends (null if not active) | [optional] 
**Endpoint** | **string** |  | [optional] 
**Tools** | [**List&lt;McpConfigGet200ResponseToolsInner&gt;**](McpConfigGet200ResponseToolsInner.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

