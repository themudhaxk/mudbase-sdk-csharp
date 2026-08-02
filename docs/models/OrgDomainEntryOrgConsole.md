# Mudbase.SDK.Model.OrgDomainEntryOrgConsole
Org API compact domain row: use **`dnsRecords`** for the Mudbase ownership TXT (purpose `mudbase_ownership`) and routing CNAME. Omits `hostnameNormalized`, `verificationToken`, `dnsTxtHost`, and `dnsTxtValue`. Omits `cloudflareEdge` when Cloudflare SaaS is not configured. Optional keys with no value are omitted from JSON responses.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | [optional] 
**Hostname** | **string** |  | [optional] 
**Status** | **string** |  | [optional] 
**IsPrimary** | **bool** |  | [optional] 
**Source** | **string** |  | [optional] 
**CreatedAt** | **DateTime** |  | [optional] 
**VerifiedAt** | **DateTime** |  | [optional] 
**LastVerifiedAt** | **DateTime** |  | [optional] 
**CnameSubmittedAt** | **DateTime** |  | [optional] 
**CnameApprovedAt** | **DateTime** |  | [optional] 
**CustomDomainVerificationStep** | **int** |  | [optional] 
**RoutingCnameTarget** | **string** |  | [optional] 
**DnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) |  | [optional] 
**PlatformActivationPending** | **bool** |  | [optional] 
**CustomDomainLiveForApiTraffic** | **bool** |  | [optional] 
**CloudflareEdge** | [**OrgCloudflareEdgeHints**](OrgCloudflareEdgeHints.md) |  | [optional] 
**FlyCertificateStatus** | **string** |  | [optional] 
**PlatformDnsVerification** | [**OrgPlatformDnsVerificationCustomer**](OrgPlatformDnsVerificationCustomer.md) |  | [optional] 
**PlatformDnsVerificationSubmittedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

