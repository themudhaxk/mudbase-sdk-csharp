# Mudbase.SDK.Model.AdminOrgLimitsPatchRequest
Partial org limit overrides for platform admins. At least one property required. Keys match `PLANS[*].limits` in the backend; integers are non-negative or null for unlimited. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Projects** | **int** |  | [optional] 
**Storage** | **int** |  | [optional] 
**Bandwidth** | **int** |  | [optional] 
**ApiCalls** | **int** |  | [optional] 
**Buckets** | **int** |  | [optional] 
**Collections** | **int** |  | [optional] 
**RealtimeConnections** | **int** |  | [optional] 
**RealtimeMessages** | **int** |  | [optional] 
**ChatMessagesPerMonth** | **int** |  | [optional] 
**MonitoredWallets** | **int** |  | [optional] 
**WalletWebhooksPerOrg** | **int** |  | [optional] 
**ApiKeysPerProject** | **int** |  | [optional] 
**WebhooksPerProject** | **int** |  | [optional] 
**FunctionsPerProject** | **int** |  | [optional] 
**FunctionInvocationsPerMonth** | **int** |  | [optional] 
**MessagingMessagesPerMonth** | **int** |  | [optional] 
**SmsPerMonth** | **int** |  | [optional] 
**ChatChannelsPerProject** | **int** |  | [optional] 
**BackupsPerProject** | **int** |  | [optional] 
**RestoresPerMonth** | **int** |  | [optional] 
**IntegrationsPerProject** | **int** |  | [optional] 
**RolesPerOrg** | **int** |  | [optional] 
**AlertsPerProject** | **int** |  | [optional] 
**BlockchainChains** | **int** |  | [optional] 
**TeamUsers** | **int** |  | [optional] 
**BugAnalysis** | [**AdminOrgLimitsPatchRequestBugAnalysis**](AdminOrgLimitsPatchRequestBugAnalysis.md) |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

