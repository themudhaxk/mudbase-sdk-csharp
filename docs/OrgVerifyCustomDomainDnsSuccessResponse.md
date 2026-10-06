# Mudbase.SDK.Model.OrgVerifyCustomDomainDnsSuccessResponse

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Success** | **bool** |  | 
**Hostname** | **string** |  | 
**Status** | **string** | Domain row status after check (typically cname_pending_staff after first TXT success from pending/failed; legacy dns_verified possible) | 
**VerificationToken** | **string** |  | 
**ChallengeHost** | **string** | Same as dnsTxtHost (_mudbase-verify.&lt;hostname&gt;) | 
**ExpectedTxt** | **string** | Same as dnsTxtValue | 
**DnsTxtHost** | **string** |  | 
**DnsTxtValue** | **string** |  | 
**Edge** | [**OrgEdgeHints**](OrgEdgeHints.md) |  | [optional] 
**DnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) | Same shape as &#x60;OrgDomainEntryWithDns.dnsRecords&#x60; when certificate provisioning ran after this successful verify; omit or empty when provisioning is disabled or not yet run. | [optional] 
**FlyCertificateStatus** | **string** | Managed certificate status after verify when provisioning is active; null otherwise | [optional] 
**FlyAcmeEnabled** | **bool** | True when automated managed-certificate provisioning is configured for this deployment. | [optional] 
**FlyAcmeDisabledReason** | **string** | When &#x60;flyAcmeEnabled&#x60; is false, why automated provisioning did not run (ops misconfiguration hint). | [optional] 
**FlyProvisionError** | **string** | When provisioning is enabled but certificate issuance failed, the provider error message for support; null on success. | [optional] 
**FlyLegacyStaffPipeline** | **bool** | When true, the legacy staff pipeline is on: status may stay &#x60;cname_pending_staff&#x60; and staff approve-cname is required even if certificate provisioning succeeds. | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

