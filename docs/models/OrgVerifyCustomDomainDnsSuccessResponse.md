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
**Cloudflare** | [**OrgCloudflareEdgeHints**](OrgCloudflareEdgeHints.md) |  | [optional] 
**DnsRecords** | [**List&lt;OrgDnsRecord&gt;**](OrgDnsRecord.md) | Same shape as &#x60;OrgDomainEntryWithDns.dnsRecords&#x60; when Fly ACME ran after this successful verify; omit or empty when Fly ACME is disabled or not provisioned. | [optional] 
**FlyCertificateStatus** | **string** | Fly certificate status after verify when Fly ACME is active; null otherwise | [optional] 
**FlyAcmeEnabled** | **bool** | True when Fly ACME would call the Certificates API (token, app, CUSTOM_DOMAIN_FLY_ACME_ENABLED). | [optional] 
**FlyAcmeDisabledReason** | **string** | When &#x60;flyAcmeEnabled&#x60; is false, why Fly ACME did not run (ops misconfiguration hint). | [optional] 
**FlyProvisionError** | **string** | When Fly ACME is enabled but POST acme failed, Fly API error message for support; null on success. | [optional] 
**FlyLegacyStaffPipeline** | **bool** | When true, &#x60;CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE&#x60; is on — status may stay &#x60;cname_pending_staff&#x60; and staff approve-cname is required even if Fly provision succeeds. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

