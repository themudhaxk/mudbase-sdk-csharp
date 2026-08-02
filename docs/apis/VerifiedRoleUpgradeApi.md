# Mudbase.SDK.Api.VerifiedRoleUpgradeApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**VerifiedRoleUpgrade**](VerifiedRoleUpgradeApi.md#verifiedroleupgrade) | **POST** /api/orgs/{orgId}/users/{userId}/upgrade | Verified role upgrade with payment verification |

<a id="verifiedroleupgrade"></a>
# **VerifiedRoleUpgrade**
> VerifiedRoleUpgrade200Response VerifiedRoleUpgrade (string orgId, string userId, VerifiedRoleUpgradeRequest verifiedRoleUpgradeRequest)

Verified role upgrade with payment verification

Upgrade user role after verifying payment and KYC. Prevents replay attacks.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |
| **verifiedRoleUpgradeRequest** | [**VerifiedRoleUpgradeRequest**](VerifiedRoleUpgradeRequest.md) |  |  |

### Return type

[**VerifiedRoleUpgrade200Response**](VerifiedRoleUpgrade200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role upgraded successfully |  -  |
| **403** | Payment verification failed or insufficient permissions |  -  |
| **404** | User or role not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

