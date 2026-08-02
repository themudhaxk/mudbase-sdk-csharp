# Mudbase.SDK.Model.OrgPlatformDnsVerificationCustomer
Additional DNS record from platform staff (non-Fly path), or first Fly TXT shim when Fly ACME is enabled. Prefer `dnsRecords` for full instructions. `staffNote` may appear in admin org detail only.

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**RecordType** | **string** |  | [optional] 
**RecordName** | **string** |  | [optional] 
**RecordValue** | **string** |  | [optional] 
**TtlSeconds** | **int?** |  | [optional] 
**StaffNote** | **string** |  | [optional] 
**UpdatedAt** | **DateTime?** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

