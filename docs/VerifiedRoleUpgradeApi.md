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

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using Mudbase.SDK.Api;
using Mudbase.SDK.Client;
using Mudbase.SDK.Model;

namespace Example
{
    public class VerifiedRoleUpgradeExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";
            // Configure Bearer token for authorization: ProjectBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new VerifiedRoleUpgradeApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var userId = "userId_example";  // string | 
            var verifiedRoleUpgradeRequest = new VerifiedRoleUpgradeRequest(); // VerifiedRoleUpgradeRequest | 

            try
            {
                // Verified role upgrade with payment verification
                VerifiedRoleUpgrade200Response result = apiInstance.VerifiedRoleUpgrade(orgId, userId, verifiedRoleUpgradeRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling VerifiedRoleUpgradeApi.VerifiedRoleUpgrade: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the VerifiedRoleUpgradeWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Verified role upgrade with payment verification
    ApiResponse<VerifiedRoleUpgrade200Response> response = apiInstance.VerifiedRoleUpgradeWithHttpInfo(orgId, userId, verifiedRoleUpgradeRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling VerifiedRoleUpgradeApi.VerifiedRoleUpgradeWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

