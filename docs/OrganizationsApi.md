# Mudbase.SDK.Api.OrganizationsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddOrgCustomDomain**](OrganizationsApi.md#addorgcustomdomain) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains | Add a custom domain |
| [**CreateOrganization**](OrganizationsApi.md#createorganization) | **POST** /api/orgs | ~~Create new organization~~ (disabled) |
| [**DeleteOrgCustomDomain**](OrganizationsApi.md#deleteorgcustomdomain) | **DELETE** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Remove a custom domain |
| [**DeleteOrganization**](OrganizationsApi.md#deleteorganization) | **DELETE** /api/orgs/{orgId} | Delete organization |
| [**DeleteSubOrganization**](OrganizationsApi.md#deletesuborganization) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Delete sub-organization~~ (deprecated) |
| [**GetOrgCustomDomainDnsInstructions**](OrganizationsApi.md#getorgcustomdomaindnsinstructions) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/dns-instructions | Get DNS TXT record instructions for one hostname |
| [**GetOrganization**](OrganizationsApi.md#getorganization) | **GET** /api/orgs/{orgId} | Get organization details by ID |
| [**GetOrganizationMembers**](OrganizationsApi.md#getorganizationmembers) | **GET** /api/orgs/{orgId}/members | Get organization members |
| [**GetOrganizationUsage**](OrganizationsApi.md#getorganizationusage) | **GET** /api/orgs/{orgId}/usage | Get organization usage and billing |
| [**GetOrganizationUsers**](OrganizationsApi.md#getorganizationusers) | **GET** /api/orgs/{orgId}/users | List organization users with metadata |
| [**GetProjectUsers**](OrganizationsApi.md#getprojectusers) | **GET** /api/orgs/{orgId}/projects/{projectId}/users | List project users with metadata |
| [**GetSubOrganizations**](OrganizationsApi.md#getsuborganizations) | **GET** /api/orgs/{orgId}/suborgs | ~~Get sub-organizations~~ (deprecated) |
| [**GetUserOverview**](OrganizationsApi.md#getuseroverview) | **GET** /api/orgs/{orgId}/users/{userId}/overview | Get user overview and data footprint |
| [**InternalCustomDomainAddon**](OrganizationsApi.md#internalcustomdomainaddon) | **POST** /internal/org/custom-domain-addon | Enable/disable Growth/Scale custom domain add-on (internal) |
| [**InternalCustomDomainSweepStatus**](OrganizationsApi.md#internalcustomdomainsweepstatus) | **GET** /internal/custom-domain/sweep-status | Custom domain background sweep status (internal) |
| [**InternalDomainDnsRecheckBatch**](OrganizationsApi.md#internaldomaindnsrecheckbatch) | **POST** /internal/domain-dns/recheck-batch | Batch DNS re-verification for drift (internal) |
| [**InternalProvisionEnterprise**](OrganizationsApi.md#internalprovisionenterprise) | **POST** /internal/provision-enterprise | Provision enterprise dedicated API/DB (internal) |
| [**InviteSubOrganizationMember**](OrganizationsApi.md#invitesuborganizationmember) | **POST** /api/orgs/{orgId}/suborgs/{suborgId}/invite | ~~Invite member to sub-organization~~ (deprecated) |
| [**InviteTeamMember**](OrganizationsApi.md#inviteteammember) | **POST** /api/orgs/{orgId}/invite | Invite team member to organization |
| [**ListOrgCustomDomains**](OrganizationsApi.md#listorgcustomdomains) | **GET** /api/orgs/{orgId}/projects/{projectId}/domains | List custom domains and DNS verification hints |
| [**ListOrganizations**](OrganizationsApi.md#listorganizations) | **GET** /api/orgs | Get all organizations for user |
| [**OrgCustomDomainPlatformReady**](OrganizationsApi.md#orgcustomdomainplatformready) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/platform-ready | Notify platform ops that hosting or edge work is ready (email) |
| [**OrgCustomDomainSubmitCname**](OrganizationsApi.md#orgcustomdomainsubmitcname) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-cname | Custom domain step 2 (optional): org confirms routing CNAME was added |
| [**OrgCustomDomainSubmitPlatformDnsVerificationDeprecated**](OrganizationsApi.md#orgcustomdomainsubmitplatformdnsverificationdeprecated) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/submit-platform-dns-verification | Deprecated — use POST .../verify-platform-dns |
| [**OrgCustomDomainVerifyPlatformDns**](OrganizationsApi.md#orgcustomdomainverifyplatformdns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-platform-dns | Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness) |
| [**PatchOrgCustomDomain**](OrganizationsApi.md#patchorgcustomdomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname} | Update domain status or regenerate verification token |
| [**RemoveSubOrganizationMember**](OrganizationsApi.md#removesuborganizationmember) | **DELETE** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId} | ~~Remove member from sub-organization~~ (deprecated) |
| [**RemoveTeamMember**](OrganizationsApi.md#removeteammember) | **DELETE** /api/orgs/{orgId}/members/{userId} | Remove team member from organization |
| [**SetOrgPrimaryDomain**](OrganizationsApi.md#setorgprimarydomain) | **PATCH** /api/orgs/{orgId}/projects/{projectId}/domains/primary | Set primary custom domain |
| [**UpdateMemberRole**](OrganizationsApi.md#updatememberrole) | **PATCH** /api/orgs/{orgId}/members/{userId}/role | Update member role |
| [**UpdateOrganization**](OrganizationsApi.md#updateorganization) | **PATCH** /api/orgs/{orgId} | Update organization |
| [**UpdateOrganizationPlan**](OrganizationsApi.md#updateorganizationplan) | **PATCH** /api/orgs/plan/{orgId} | Update organization plan |
| [**UpdateSubOrganization**](OrganizationsApi.md#updatesuborganization) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId} | ~~Update sub-organization~~ (deprecated) |
| [**UpdateSubOrganizationMemberRole**](OrganizationsApi.md#updatesuborganizationmemberrole) | **PATCH** /api/orgs/{orgId}/suborgs/{suborgId}/members/{userId}/role | ~~Update sub-organization member role~~ (deprecated) |
| [**UpdateUserAccountStatus**](OrganizationsApi.md#updateuseraccountstatus) | **PATCH** /api/orgs/{orgId}/users/{userId}/status | Update user account status (activate or suspend) |
| [**VerifyOrgCustomDomainDns**](OrganizationsApi.md#verifyorgcustomdomaindns) | **POST** /api/orgs/{orgId}/projects/{projectId}/domains/{hostname}/verify-dns | Verify domain ownership via DNS TXT |

<a id="addorgcustomdomain"></a>
# **AddOrgCustomDomain**
> OrgAddDomainResponse AddOrgCustomDomain (string orgId, string projectId, AddOrgDomainRequest addOrgDomainRequest)

Add a custom domain

Creates a pending domain row; the response **`domain`** uses the compact **`OrgDomainEntryOrgConsole`** shape (**`dnsRecords`** includes the Mudbase ownership TXT). **`dnsRecords`** may include Mudbase TXT and routing CNAME only until Mudbase TXT succeeds and Fly ACME (if enabled) provisions a certificate. **`flyCertificateStatus`** is typically omitted until Fly ACME runs after first successful **`verify-dns`**. 

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
    public class AddOrgCustomDomainExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var addOrgDomainRequest = new AddOrgDomainRequest(); // AddOrgDomainRequest | 

            try
            {
                // Add a custom domain
                OrgAddDomainResponse result = apiInstance.AddOrgCustomDomain(orgId, projectId, addOrgDomainRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.AddOrgCustomDomain: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the AddOrgCustomDomainWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Add a custom domain
    ApiResponse<OrgAddDomainResponse> response = apiInstance.AddOrgCustomDomainWithHttpInfo(orgId, projectId, addOrgDomainRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.AddOrgCustomDomainWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **addOrgDomainRequest** | [**AddOrgDomainRequest**](AddOrgDomainRequest.md) |  |  |

### Return type

[**OrgAddDomainResponse**](OrgAddDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Domain created; includes dnsRecords and human-readable instructions (no extra GET required). |  -  |
| **400** | Validation, limit, or hostname_in_use |  -  |
| **429** | domain_rate_limited |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createorganization"></a>
# **CreateOrganization**
> void CreateOrganization (CreateOrganizationRequest createOrganizationRequest)

~~Create new organization~~ (disabled)

~~Create a new organization.~~ This endpoint is disabled and kept only for backward compatibility in documentation. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class CreateOrganizationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var createOrganizationRequest = new CreateOrganizationRequest(); // CreateOrganizationRequest | 

            try
            {
                // ~~Create new organization~~ (disabled)
                apiInstance.CreateOrganization(createOrganizationRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.CreateOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Create new organization~~ (disabled)
    apiInstance.CreateOrganizationWithHttpInfo(createOrganizationRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.CreateOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createOrganizationRequest** | [**CreateOrganizationRequest**](CreateOrganizationRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **403** | Organization creation disabled |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteorgcustomdomain"></a>
# **DeleteOrgCustomDomain**
> void DeleteOrgCustomDomain (string orgId, string projectId, string hostname)

Remove a custom domain

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
    public class DeleteOrgCustomDomainExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Remove a custom domain
                apiInstance.DeleteOrgCustomDomain(orgId, projectId, hostname);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.DeleteOrgCustomDomain: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteOrgCustomDomainWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Remove a custom domain
    apiInstance.DeleteOrgCustomDomainWithHttpInfo(orgId, projectId, hostname);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.DeleteOrgCustomDomainWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Removed |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteorganization"></a>
# **DeleteOrganization**
> DeleteOrganization200Response DeleteOrganization (string orgId)

Delete organization

Delete an organization permanently. This is a destructive operation. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class DeleteOrganizationExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 

            try
            {
                // Delete organization
                DeleteOrganization200Response result = apiInstance.DeleteOrganization(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.DeleteOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete organization
    ApiResponse<DeleteOrganization200Response> response = apiInstance.DeleteOrganizationWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.DeleteOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**DeleteOrganization200Response**](DeleteOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization deleted |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletesuborganization"></a>
# **DeleteSubOrganization**
> DeleteSubOrganization200Response DeleteSubOrganization (string orgId, string suborgId)

~~Delete sub-organization~~ (deprecated)

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
    public class DeleteSubOrganizationExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var suborgId = 685acbe0e129932fbb7a0fc4;  // string | 

            try
            {
                // ~~Delete sub-organization~~ (deprecated)
                DeleteSubOrganization200Response result = apiInstance.DeleteSubOrganization(orgId, suborgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.DeleteSubOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteSubOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Delete sub-organization~~ (deprecated)
    ApiResponse<DeleteSubOrganization200Response> response = apiInstance.DeleteSubOrganizationWithHttpInfo(orgId, suborgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.DeleteSubOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **suborgId** | **string** |  |  |

### Return type

[**DeleteSubOrganization200Response**](DeleteSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Sub-organization deleted |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getorgcustomdomaindnsinstructions"></a>
# **GetOrgCustomDomainDnsInstructions**
> OrgDnsInstructionsResponse GetOrgCustomDomainDnsInstructions (string orgId, string projectId, string hostname)

Get DNS TXT record instructions for one hostname

Returns the same shape as list/add for one hostname (URL-encode `hostname` in the path), including **`dnsRecords`** and **`flyCertificateStatus`** when applicable. See **`listOrgCustomDomains`** for how Fly ACME and Cloudflare SaaS affect those fields. 

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
    public class GetOrgCustomDomainDnsInstructionsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Get DNS TXT record instructions for one hostname
                OrgDnsInstructionsResponse result = apiInstance.GetOrgCustomDomainDnsInstructions(orgId, projectId, hostname);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetOrgCustomDomainDnsInstructions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOrgCustomDomainDnsInstructionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get DNS TXT record instructions for one hostname
    ApiResponse<OrgDnsInstructionsResponse> response = apiInstance.GetOrgCustomDomainDnsInstructionsWithHttpInfo(orgId, projectId, hostname);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetOrgCustomDomainDnsInstructionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

[**OrgDnsInstructionsResponse**](OrgDnsInstructionsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain row with DNS hints |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **404** | domain_not_found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getorganization"></a>
# **GetOrganization**
> Organization GetOrganization (string orgId)

Get organization details by ID

Get organization details by ID. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class GetOrganizationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 

            try
            {
                // Get organization details by ID
                Organization result = apiInstance.GetOrganization(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get organization details by ID
    ApiResponse<Organization> response = apiInstance.GetOrganizationWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**Organization**](Organization.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization details |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getorganizationmembers"></a>
# **GetOrganizationMembers**
> GetOrganizationMembers200Response GetOrganizationMembers (string orgId)

Get organization members

Get all members of an organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

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
    public class GetOrganizationMembersExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 

            try
            {
                // Get organization members
                GetOrganizationMembers200Response result = apiInstance.GetOrganizationMembers(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetOrganizationMembers: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOrganizationMembersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get organization members
    ApiResponse<GetOrganizationMembers200Response> response = apiInstance.GetOrganizationMembersWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetOrganizationMembersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**GetOrganizationMembers200Response**](GetOrganizationMembers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization members |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getorganizationusage"></a>
# **GetOrganizationUsage**
> GetOrganizationUsage200Response GetOrganizationUsage (string orgId)

Get organization usage and billing

Get usage statistics and billing information for an organization. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class GetOrganizationUsageExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 

            try
            {
                // Get organization usage and billing
                GetOrganizationUsage200Response result = apiInstance.GetOrganizationUsage(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetOrganizationUsage: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOrganizationUsageWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get organization usage and billing
    ApiResponse<GetOrganizationUsage200Response> response = apiInstance.GetOrganizationUsageWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetOrganizationUsageWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**GetOrganizationUsage200Response**](GetOrganizationUsage200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage and billing information |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getorganizationusers"></a>
# **GetOrganizationUsers**
> GetOrganizationUsers200Response GetOrganizationUsers (string orgId, string? status = null)

List organization users with metadata

Get all users in the organization with metadata (email, full name, role, accountStatus, phone, lastLogin, etc.). Optional query `status` filters by accountStatus (pending, active, suspended). Requires organization access and owner or admin role. 

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
    public class GetOrganizationUsersExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var status = "pending";  // string? | Filter by account status (pending, active, suspended) (optional) 

            try
            {
                // List organization users with metadata
                GetOrganizationUsers200Response result = apiInstance.GetOrganizationUsers(orgId, status);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetOrganizationUsers: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetOrganizationUsersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List organization users with metadata
    ApiResponse<GetOrganizationUsers200Response> response = apiInstance.GetOrganizationUsersWithHttpInfo(orgId, status);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetOrganizationUsersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **status** | **string?** | Filter by account status (pending, active, suspended) | [optional]  |

### Return type

[**GetOrganizationUsers200Response**](GetOrganizationUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization users with metadata |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprojectusers"></a>
# **GetProjectUsers**
> GetProjectUsers200Response GetProjectUsers (string orgId, string projectId, string? status = null)

List project users with metadata

Get all users in a project with metadata (email, full name, role, accountStatus, etc.). Optional query `status` filters by accountStatus. Project must belong to the organization. Requires owner or admin role. 

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
    public class GetProjectUsersExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var projectId = 685ad30be129932fbb7a1047;  // string | 
            var status = "pending";  // string? | Filter by account status (pending, active, suspended) (optional) 

            try
            {
                // List project users with metadata
                GetProjectUsers200Response result = apiInstance.GetProjectUsers(orgId, projectId, status);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetProjectUsers: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProjectUsersWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List project users with metadata
    ApiResponse<GetProjectUsers200Response> response = apiInstance.GetProjectUsersWithHttpInfo(orgId, projectId, status);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetProjectUsersWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **status** | **string?** | Filter by account status (pending, active, suspended) | [optional]  |

### Return type

[**GetProjectUsers200Response**](GetProjectUsers200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Project users with metadata |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getsuborganizations"></a>
# **GetSubOrganizations**
> GetSubOrganizations200Response GetSubOrganizations (string orgId)

~~Get sub-organizations~~ (deprecated)

Get all sub-organizations under a parent organization. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class GetSubOrganizationsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 

            try
            {
                // ~~Get sub-organizations~~ (deprecated)
                GetSubOrganizations200Response result = apiInstance.GetSubOrganizations(orgId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetSubOrganizations: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetSubOrganizationsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Get sub-organizations~~ (deprecated)
    ApiResponse<GetSubOrganizations200Response> response = apiInstance.GetSubOrganizationsWithHttpInfo(orgId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetSubOrganizationsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |

### Return type

[**GetSubOrganizations200Response**](GetSubOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of sub-organizations |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getuseroverview"></a>
# **GetUserOverview**
> GetUserOverview200Response GetUserOverview (string orgId, string userId)

Get user overview and data footprint

Get a user's profile plus footprint (files count/size, sessions, API keys, collections in project). Use for dashboard to see everything tied to the user. Requires owner or admin role. 

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
    public class GetUserOverviewExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var userId = "userId_example";  // string | 

            try
            {
                // Get user overview and data footprint
                GetUserOverview200Response result = apiInstance.GetUserOverview(orgId, userId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.GetUserOverview: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetUserOverviewWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get user overview and data footprint
    ApiResponse<GetUserOverview200Response> response = apiInstance.GetUserOverviewWithHttpInfo(orgId, userId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.GetUserOverviewWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |

### Return type

[**GetUserOverview200Response**](GetUserOverview200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User and footprint |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="internalcustomdomainaddon"></a>
# **InternalCustomDomainAddon**
> void InternalCustomDomainAddon (InternalCustomDomainAddonRequest internalCustomDomainAddonRequest)

Enable/disable Growth/Scale custom domain add-on (internal)

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
    public class InternalCustomDomainAddonExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: InternalApiKey
            config.AddApiKey("X-Internal-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Internal-Api-Key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var internalCustomDomainAddonRequest = new InternalCustomDomainAddonRequest(); // InternalCustomDomainAddonRequest | 

            try
            {
                // Enable/disable Growth/Scale custom domain add-on (internal)
                apiInstance.InternalCustomDomainAddon(internalCustomDomainAddonRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InternalCustomDomainAddon: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InternalCustomDomainAddonWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Enable/disable Growth/Scale custom domain add-on (internal)
    apiInstance.InternalCustomDomainAddonWithHttpInfo(internalCustomDomainAddonRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InternalCustomDomainAddonWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **internalCustomDomainAddonRequest** | [**InternalCustomDomainAddonRequest**](InternalCustomDomainAddonRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="internalcustomdomainsweepstatus"></a>
# **InternalCustomDomainSweepStatus**
> void InternalCustomDomainSweepStatus ()

Custom domain background sweep status (internal)

Returns the last automated custom-domain sweep (TXT recheck + Fly ACME retry), job env flags, and Fly deploy troubleshooting hints when the proxy reports the app is not listening on 0.0.0.0:PORT. Requires header `X-Internal-Api-Key` (same as other /internal routes).

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
    public class InternalCustomDomainSweepStatusExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: InternalApiKey
            config.AddApiKey("X-Internal-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Internal-Api-Key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);

            try
            {
                // Custom domain background sweep status (internal)
                apiInstance.InternalCustomDomainSweepStatus();
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InternalCustomDomainSweepStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InternalCustomDomainSweepStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Custom domain background sweep status (internal)
    apiInstance.InternalCustomDomainSweepStatusWithHttpInfo();
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InternalCustomDomainSweepStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

void (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | sweep payload, jobConfig, flyHttpListenTroubleshooting |  -  |
| **401** | Unauthorized |  -  |
| **503** | INTERNAL_API_KEY not configured |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="internaldomaindnsrecheckbatch"></a>
# **InternalDomainDnsRecheckBatch**
> void InternalDomainDnsRecheckBatch (InternalDomainDnsRecheckBatchRequest? internalDomainDnsRecheckBatchRequest = null)

Batch DNS re-verification for drift (internal)

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
    public class InternalDomainDnsRecheckBatchExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: InternalApiKey
            config.AddApiKey("X-Internal-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Internal-Api-Key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var internalDomainDnsRecheckBatchRequest = new InternalDomainDnsRecheckBatchRequest?(); // InternalDomainDnsRecheckBatchRequest? |  (optional) 

            try
            {
                // Batch DNS re-verification for drift (internal)
                apiInstance.InternalDomainDnsRecheckBatch(internalDomainDnsRecheckBatchRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InternalDomainDnsRecheckBatch: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InternalDomainDnsRecheckBatchWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Batch DNS re-verification for drift (internal)
    apiInstance.InternalDomainDnsRecheckBatchWithHttpInfo(internalDomainDnsRecheckBatchRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InternalDomainDnsRecheckBatchWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **internalDomainDnsRecheckBatchRequest** | [**InternalDomainDnsRecheckBatchRequest?**](InternalDomainDnsRecheckBatchRequest?.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Summary counts |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="internalprovisionenterprise"></a>
# **InternalProvisionEnterprise**
> void InternalProvisionEnterprise (ProvisionEnterpriseRequest provisionEnterpriseRequest)

Provision enterprise dedicated API/DB (internal)

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
    public class InternalProvisionEnterpriseExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure API key authorization: InternalApiKey
            config.AddApiKey("X-Internal-Api-Key", "YOUR_API_KEY");
            // Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
            // config.AddApiKeyPrefix("X-Internal-Api-Key", "Bearer");

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var provisionEnterpriseRequest = new ProvisionEnterpriseRequest(); // ProvisionEnterpriseRequest | 

            try
            {
                // Provision enterprise dedicated API/DB (internal)
                apiInstance.InternalProvisionEnterprise(provisionEnterpriseRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InternalProvisionEnterprise: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InternalProvisionEnterpriseWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Provision enterprise dedicated API/DB (internal)
    apiInstance.InternalProvisionEnterpriseWithHttpInfo(provisionEnterpriseRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InternalProvisionEnterpriseWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **provisionEnterpriseRequest** | [**ProvisionEnterpriseRequest**](ProvisionEnterpriseRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[InternalApiKey](../README.md#InternalApiKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Applied or idempotent no-op |  -  |
| **403** | not_enterprise_plan |  -  |
| **409** | provision_conflict |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="invitesuborganizationmember"></a>
# **InviteSubOrganizationMember**
> InviteSubOrganizationMember200Response InviteSubOrganizationMember (string orgId, string suborgId, InviteMemberRequest inviteMemberRequest)

~~Invite member to sub-organization~~ (deprecated)

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
    public class InviteSubOrganizationMemberExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var suborgId = 685acbe0e129932fbb7a0fc4;  // string | 
            var inviteMemberRequest = new InviteMemberRequest(); // InviteMemberRequest | 

            try
            {
                // ~~Invite member to sub-organization~~ (deprecated)
                InviteSubOrganizationMember200Response result = apiInstance.InviteSubOrganizationMember(orgId, suborgId, inviteMemberRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InviteSubOrganizationMember: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InviteSubOrganizationMemberWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Invite member to sub-organization~~ (deprecated)
    ApiResponse<InviteSubOrganizationMember200Response> response = apiInstance.InviteSubOrganizationMemberWithHttpInfo(orgId, suborgId, inviteMemberRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InviteSubOrganizationMemberWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **suborgId** | **string** |  |  |
| **inviteMemberRequest** | [**InviteMemberRequest**](InviteMemberRequest.md) |  |  |

### Return type

[**InviteSubOrganizationMember200Response**](InviteSubOrganizationMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invitation sent |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="inviteteammember"></a>
# **InviteTeamMember**
> InviteTeamMember200Response InviteTeamMember (string orgId, InviteMemberRequest inviteMemberRequest)

Invite team member to organization

Send an invitation to a user to join the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class InviteTeamMemberExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var inviteMemberRequest = new InviteMemberRequest(); // InviteMemberRequest | 

            try
            {
                // Invite team member to organization
                InviteTeamMember200Response result = apiInstance.InviteTeamMember(orgId, inviteMemberRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.InviteTeamMember: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the InviteTeamMemberWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Invite team member to organization
    ApiResponse<InviteTeamMember200Response> response = apiInstance.InviteTeamMemberWithHttpInfo(orgId, inviteMemberRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.InviteTeamMemberWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **inviteMemberRequest** | [**InviteMemberRequest**](InviteMemberRequest.md) |  |  |

### Return type

[**InviteTeamMember200Response**](InviteTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Invitation sent |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listorgcustomdomains"></a>
# **ListOrgCustomDomains**
> OrgDomainsListResponse ListOrgCustomDomains (string orgId, string projectId)

List custom domains and DNS verification hints

Returns allowed hostnames for **this project**, primary hostname (per project), API base URL, and per-domain DNS guidance.  Each row uses **`dnsRecords`** for the Mudbase ownership TXT (purpose **`mudbase_ownership`**) and routing **CNAME** from Fly **`dns_requirements.cname`** when Fly ACME has provisioned (else fallback **`CUSTOM_DOMAIN_API_CNAME_TARGET`**), and—when Fly ACME is enabled (**`FLY_API_TOKEN`** + **`CUSTOM_DOMAIN_FLY_ACME_ENABLED`**)—Fly rows (`fly_ownership`, `acme_challenge`, etc.) after the org has passed Mudbase TXT at least once. **`flyCertificateStatus`** mirrors Fly’s certificate state when ACME automation is on (e.g. `pending_validation`, `active`).  **`cloudflareEdge`** appears only when Cloudflare SSL-for-SaaS env is configured. Fly ACME and Cloudflare SaaS are mutually exclusive on the server.  Requires Growth, Scale, or Enterprise plan (custom domains included in plan features). 

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
    public class ListOrgCustomDomainsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 

            try
            {
                // List custom domains and DNS verification hints
                OrgDomainsListResponse result = apiInstance.ListOrgCustomDomains(orgId, projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.ListOrgCustomDomains: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListOrgCustomDomainsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List custom domains and DNS verification hints
    ApiResponse<OrgDomainsListResponse> response = apiInstance.ListOrgCustomDomainsWithHttpInfo(orgId, projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.ListOrgCustomDomainsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |

### Return type

[**OrgDomainsListResponse**](OrgDomainsListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain list and hints |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listorganizations"></a>
# **ListOrganizations**
> ListOrganizations200Response ListOrganizations ()

Get all organizations for user

Get all organizations the authenticated user belongs to. Requires: OrgBearerAuth (organization-level authentication only). 

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
    public class ListOrganizationsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);

            try
            {
                // Get all organizations for user
                ListOrganizations200Response result = apiInstance.ListOrganizations();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.ListOrganizations: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListOrganizationsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get all organizations for user
    ApiResponse<ListOrganizations200Response> response = apiInstance.ListOrganizationsWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.ListOrganizationsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**ListOrganizations200Response**](ListOrganizations200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of organizations |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="orgcustomdomainplatformready"></a>
# **OrgCustomDomainPlatformReady**
> void OrgCustomDomainPlatformReady (string orgId, string projectId, string hostname, OrgCustomDomainPlatformReadyRequest? orgCustomDomainPlatformReadyRequest = null)

Notify platform ops that hosting or edge work is ready (email)

Legacy optional ping: ops are emailed automatically on first successful Mudbase TXT verify. Use this only for an extra nudge. Sends an email to ops while the domain is in platform setup (after Mudbase TXT verification through later pipeline states). Recipients default to `admin@mudhaxkservices.com` and `admin@mudbase.dev` when `CUSTOM_DOMAIN_OPS_NOTIFY_EMAILS` is unset; override with that env (comma/space-separated). Returns **503** `email_provider_not_configured` if no email provider is configured (e.g. missing `ZEPTOMAIL_SEND_TOKEN`). 

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
    public class OrgCustomDomainPlatformReadyExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 
            var orgCustomDomainPlatformReadyRequest = new OrgCustomDomainPlatformReadyRequest?(); // OrgCustomDomainPlatformReadyRequest? |  (optional) 

            try
            {
                // Notify platform ops that hosting or edge work is ready (email)
                apiInstance.OrgCustomDomainPlatformReady(orgId, projectId, hostname, orgCustomDomainPlatformReadyRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainPlatformReady: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the OrgCustomDomainPlatformReadyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Notify platform ops that hosting or edge work is ready (email)
    apiInstance.OrgCustomDomainPlatformReadyWithHttpInfo(orgId, projectId, hostname, orgCustomDomainPlatformReadyRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainPlatformReadyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |
| **orgCustomDomainPlatformReadyRequest** | [**OrgCustomDomainPlatformReadyRequest?**](OrgCustomDomainPlatformReadyRequest?.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Ops notified |  -  |
| **400** | custom_domain_invalid_state |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **503** | email_provider_not_configured — email provider not configured on the server |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="orgcustomdomainsubmitcname"></a>
# **OrgCustomDomainSubmitCname**
> OrgPatchDomainResponse OrgCustomDomainSubmitCname (string orgId, string projectId, string hostname)

Custom domain step 2 (optional): org confirms routing CNAME was added

Usually unnecessary. With Fly ACME default automation, Mudbase TXT verify may already set `cname_approved`. Legacy pipelines may queue `cname_pending_staff` until staff **`approve-cname`**. Use **`routingCnameTarget`** from **`GET .../projects/{projectId}/domains`** (Fly **`dns_requirements.cname`** when provisioned, else **`CUSTOM_DOMAIN_API_CNAME_TARGET`**). 

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
    public class OrgCustomDomainSubmitCnameExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Custom domain step 2 (optional): org confirms routing CNAME was added
                OrgPatchDomainResponse result = apiInstance.OrgCustomDomainSubmitCname(orgId, projectId, hostname);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainSubmitCname: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the OrgCustomDomainSubmitCnameWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Custom domain step 2 (optional): org confirms routing CNAME was added
    ApiResponse<OrgPatchDomainResponse> response = apiInstance.OrgCustomDomainSubmitCnameWithHttpInfo(orgId, projectId, hostname);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainSubmitCnameWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated domain row |  -  |
| **400** | custom_domain_invalid_state |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="orgcustomdomainsubmitplatformdnsverificationdeprecated"></a>
# **OrgCustomDomainSubmitPlatformDnsVerificationDeprecated**
> OrgPatchDomainResponse OrgCustomDomainSubmitPlatformDnsVerificationDeprecated (string orgId, string projectId, string hostname)

Deprecated — use POST .../verify-platform-dns

Deprecated alias of **`orgCustomDomainVerifyPlatformDns`** (same behavior — manual TXT and/or Fly ACME path per server config).

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
    public class OrgCustomDomainSubmitPlatformDnsVerificationDeprecatedExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Deprecated — use POST .../verify-platform-dns
                OrgPatchDomainResponse result = apiInstance.OrgCustomDomainSubmitPlatformDnsVerificationDeprecated(orgId, projectId, hostname);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainSubmitPlatformDnsVerificationDeprecated: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the OrgCustomDomainSubmitPlatformDnsVerificationDeprecatedWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Deprecated — use POST .../verify-platform-dns
    ApiResponse<OrgPatchDomainResponse> response = apiInstance.OrgCustomDomainSubmitPlatformDnsVerificationDeprecatedWithHttpInfo(orgId, projectId, hostname);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainSubmitPlatformDnsVerificationDeprecatedWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Same as verify-platform-dns |  -  |
| **400** | Error |  -  |
| **503** | dns_lookup_error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="orgcustomdomainverifyplatformdns"></a>
# **OrgCustomDomainVerifyPlatformDns**
> OrgPatchDomainResponse OrgCustomDomainVerifyPlatformDns (string orgId, string projectId, string hostname)

Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness)

**Manual path (no Fly ACME):** After staff **`PATCH .../platform-dns-verification`**, the org adds the published TXT and calls this endpoint. The API resolves public TXT at **`platformDnsVerification.recordName`** and matches **`recordValue`**. On success, `status` → **`platform_dns_pending_review`** until staff **`POST .../activate`**.  **Fly ACME path (default):** When Fly ACME is enabled and **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE`** is **not** set, the org calls this after Mudbase TXT and Fly DNS rows are in place (status typically **`cname_approved`** from automated verify-dns). The API triggers Fly **`POST .../check`** and **`GET`** certificate with bounded retries. On success, `status` → **`active`** and the org may receive the activation email—**no** staff **`approve-cname`** or **`activate`** required.  **Fly legacy:** If **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE=true`**, behavior matches the older flow: staff **`approve-cname`** may be required first; after a ready Fly cert, **`status`** becomes **`active`** only when **`CUSTOM_DOMAIN_FLY_AUTO_ACTIVATE=true`**, else **`platform_dns_pending_review`** until staff **`activate`**.  **`platform_dns_verification_failed`** may include **`details.flyStatus`** / **`details.flyError`** on the Fly path. 

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
    public class OrgCustomDomainVerifyPlatformDnsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness)
                OrgPatchDomainResponse result = apiInstance.OrgCustomDomainVerifyPlatformDns(orgId, projectId, hostname);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainVerifyPlatformDns: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the OrgCustomDomainVerifyPlatformDnsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Custom domain step 3: verify platform DNS (manual TXT or Fly certificate readiness)
    ApiResponse<OrgPatchDomainResponse> response = apiInstance.OrgCustomDomainVerifyPlatformDnsWithHttpInfo(orgId, projectId, hostname);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.OrgCustomDomainVerifyPlatformDnsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Domain row updated (&#x60;OrgPatchDomainResponse.domain&#x60;). Manual TXT path typically sets &#x60;platform_dns_pending_review&#x60;. Fly ACME default automation: typically &#x60;active&#x60; when the certificate is ready. Fly legacy staff pipeline: may set &#x60;platform_dns_pending_review&#x60; unless &#x60;CUSTOM_DOMAIN_FLY_AUTO_ACTIVATE&#x60; is enabled. Body may include refreshed &#x60;dnsRecords&#x60; and &#x60;flyCertificateStatus&#x60; on the Fly path. |  -  |
| **400** | custom_domain_invalid_state, platform_dns_verification_failed (manual TXT mismatch or Fly cert not active yet; see response details on Fly path) |  -  |
| **401** | Unauthorized |  -  |
| **403** | Forbidden |  -  |
| **503** | dns_lookup_error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="patchorgcustomdomain"></a>
# **PatchOrgCustomDomain**
> OrgPatchDomainResponse PatchOrgCustomDomain (string orgId, string projectId, string hostname, PatchOrgDomainRequest? patchOrgDomainRequest = null)

Update domain status or regenerate verification token

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
    public class PatchOrgCustomDomainExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 
            var patchOrgDomainRequest = new PatchOrgDomainRequest?(); // PatchOrgDomainRequest? |  (optional) 

            try
            {
                // Update domain status or regenerate verification token
                OrgPatchDomainResponse result = apiInstance.PatchOrgCustomDomain(orgId, projectId, hostname, patchOrgDomainRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.PatchOrgCustomDomain: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the PatchOrgCustomDomainWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update domain status or regenerate verification token
    ApiResponse<OrgPatchDomainResponse> response = apiInstance.PatchOrgCustomDomainWithHttpInfo(orgId, projectId, hostname, patchOrgDomainRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.PatchOrgCustomDomainWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |
| **patchOrgDomainRequest** | [**PatchOrgDomainRequest?**](PatchOrgDomainRequest?.md) |  | [optional]  |

### Return type

[**OrgPatchDomainResponse**](OrgPatchDomainResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated; domain object includes dnsTxtHost and dnsTxtValue |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="removesuborganizationmember"></a>
# **RemoveSubOrganizationMember**
> RemoveTeamMember200Response RemoveSubOrganizationMember (string orgId, string suborgId, string userId)

~~Remove member from sub-organization~~ (deprecated)

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
    public class RemoveSubOrganizationMemberExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var suborgId = 685acbe0e129932fbb7a0fc4;  // string | 
            var userId = 685acbe0e129932fbb7a0fc2;  // string | 

            try
            {
                // ~~Remove member from sub-organization~~ (deprecated)
                RemoveTeamMember200Response result = apiInstance.RemoveSubOrganizationMember(orgId, suborgId, userId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.RemoveSubOrganizationMember: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RemoveSubOrganizationMemberWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Remove member from sub-organization~~ (deprecated)
    ApiResponse<RemoveTeamMember200Response> response = apiInstance.RemoveSubOrganizationMemberWithHttpInfo(orgId, suborgId, userId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.RemoveSubOrganizationMemberWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **suborgId** | **string** |  |  |
| **userId** | **string** |  |  |

### Return type

[**RemoveTeamMember200Response**](RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Member removed |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="removeteammember"></a>
# **RemoveTeamMember**
> RemoveTeamMember200Response RemoveTeamMember (string orgId, string userId)

Remove team member from organization

Remove a user from the organization. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class RemoveTeamMemberExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var userId = 685acbe0e129932fbb7a0fc2;  // string | 

            try
            {
                // Remove team member from organization
                RemoveTeamMember200Response result = apiInstance.RemoveTeamMember(orgId, userId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.RemoveTeamMember: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RemoveTeamMemberWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Remove team member from organization
    ApiResponse<RemoveTeamMember200Response> response = apiInstance.RemoveTeamMemberWithHttpInfo(orgId, userId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.RemoveTeamMemberWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |

### Return type

[**RemoveTeamMember200Response**](RemoveTeamMember200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Member removed |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="setorgprimarydomain"></a>
# **SetOrgPrimaryDomain**
> void SetOrgPrimaryDomain (string orgId, string projectId, SetOrgPrimaryDomainRequest setOrgPrimaryDomainRequest)

Set primary custom domain

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
    public class SetOrgPrimaryDomainExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var setOrgPrimaryDomainRequest = new SetOrgPrimaryDomainRequest(); // SetOrgPrimaryDomainRequest | 

            try
            {
                // Set primary custom domain
                apiInstance.SetOrgPrimaryDomain(orgId, projectId, setOrgPrimaryDomainRequest);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.SetOrgPrimaryDomain: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the SetOrgPrimaryDomainWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Set primary custom domain
    apiInstance.SetOrgPrimaryDomainWithHttpInfo(orgId, projectId, setOrgPrimaryDomainRequest);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.SetOrgPrimaryDomainWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **setOrgPrimaryDomainRequest** | [**SetOrgPrimaryDomainRequest**](SetOrgPrimaryDomainRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Primary updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatememberrole"></a>
# **UpdateMemberRole**
> UpdateMemberRole200Response UpdateMemberRole (string orgId, string userId, UpdateMemberRoleRequest updateMemberRoleRequest)

Update member role

Update a member's role in the organization. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

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
    public class UpdateMemberRoleExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var userId = 685acbe0e129932fbb7a0fc2;  // string | 
            var updateMemberRoleRequest = new UpdateMemberRoleRequest(); // UpdateMemberRoleRequest | 

            try
            {
                // Update member role
                UpdateMemberRole200Response result = apiInstance.UpdateMemberRole(orgId, userId, updateMemberRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateMemberRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateMemberRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update member role
    ApiResponse<UpdateMemberRole200Response> response = apiInstance.UpdateMemberRoleWithHttpInfo(orgId, userId, updateMemberRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateMemberRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |
| **updateMemberRoleRequest** | [**UpdateMemberRoleRequest**](UpdateMemberRoleRequest.md) |  |  |

### Return type

[**UpdateMemberRole200Response**](UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateorganization"></a>
# **UpdateOrganization**
> UpdateOrganization200Response UpdateOrganization (string orgId, UpdateOrganizationRequest updateOrganizationRequest)

Update organization

Update organization details. Requires organization-level authentication (JWT Bearer token). API keys are not supported for this endpoint. 

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
    public class UpdateOrganizationExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var updateOrganizationRequest = new UpdateOrganizationRequest(); // UpdateOrganizationRequest | 

            try
            {
                // Update organization
                UpdateOrganization200Response result = apiInstance.UpdateOrganization(orgId, updateOrganizationRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update organization
    ApiResponse<UpdateOrganization200Response> response = apiInstance.UpdateOrganizationWithHttpInfo(orgId, updateOrganizationRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **updateOrganizationRequest** | [**UpdateOrganizationRequest**](UpdateOrganizationRequest.md) |  |  |

### Return type

[**UpdateOrganization200Response**](UpdateOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Organization updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateorganizationplan"></a>
# **UpdateOrganizationPlan**
> UpdateOrganizationPlan200Response UpdateOrganizationPlan (string orgId, UpdateOrganizationPlanRequest updateOrganizationPlanRequest)

Update organization plan

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
    public class UpdateOrganizationPlanExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var updateOrganizationPlanRequest = new UpdateOrganizationPlanRequest(); // UpdateOrganizationPlanRequest | 

            try
            {
                // Update organization plan
                UpdateOrganizationPlan200Response result = apiInstance.UpdateOrganizationPlan(orgId, updateOrganizationPlanRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateOrganizationPlan: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateOrganizationPlanWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update organization plan
    ApiResponse<UpdateOrganizationPlan200Response> response = apiInstance.UpdateOrganizationPlanWithHttpInfo(orgId, updateOrganizationPlanRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateOrganizationPlanWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **updateOrganizationPlanRequest** | [**UpdateOrganizationPlanRequest**](UpdateOrganizationPlanRequest.md) |  |  |

### Return type

[**UpdateOrganizationPlan200Response**](UpdateOrganizationPlan200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Plan updated (or error if trying to upgrade to paid) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatesuborganization"></a>
# **UpdateSubOrganization**
> UpdateSubOrganization200Response UpdateSubOrganization (string orgId, string suborgId, UpdateOrganizationRequest updateOrganizationRequest)

~~Update sub-organization~~ (deprecated)

Update a sub-organization's configuration. Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 

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
    public class UpdateSubOrganizationExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var suborgId = 685acbe0e129932fbb7a0fc4;  // string | 
            var updateOrganizationRequest = new UpdateOrganizationRequest(); // UpdateOrganizationRequest | 

            try
            {
                // ~~Update sub-organization~~ (deprecated)
                UpdateSubOrganization200Response result = apiInstance.UpdateSubOrganization(orgId, suborgId, updateOrganizationRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateSubOrganization: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateSubOrganizationWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Update sub-organization~~ (deprecated)
    ApiResponse<UpdateSubOrganization200Response> response = apiInstance.UpdateSubOrganizationWithHttpInfo(orgId, suborgId, updateOrganizationRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateSubOrganizationWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **suborgId** | **string** |  |  |
| **updateOrganizationRequest** | [**UpdateOrganizationRequest**](UpdateOrganizationRequest.md) |  |  |

### Return type

[**UpdateSubOrganization200Response**](UpdateSubOrganization200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Sub-organization updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatesuborganizationmemberrole"></a>
# **UpdateSubOrganizationMemberRole**
> UpdateMemberRole200Response UpdateSubOrganizationMemberRole (string orgId, string suborgId, string userId, UpdateMemberRoleRequest updateMemberRoleRequest)

~~Update sub-organization member role~~ (deprecated)

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
    public class UpdateSubOrganizationMemberRoleExample
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
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = 685acbe0e129932fbb7a0fc3;  // string | 
            var suborgId = 685acbe0e129932fbb7a0fc4;  // string | 
            var userId = 685acbe0e129932fbb7a0fc2;  // string | 
            var updateMemberRoleRequest = new UpdateMemberRoleRequest(); // UpdateMemberRoleRequest | 

            try
            {
                // ~~Update sub-organization member role~~ (deprecated)
                UpdateMemberRole200Response result = apiInstance.UpdateSubOrganizationMemberRole(orgId, suborgId, userId, updateMemberRoleRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateSubOrganizationMemberRole: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateSubOrganizationMemberRoleWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // ~~Update sub-organization member role~~ (deprecated)
    ApiResponse<UpdateMemberRole200Response> response = apiInstance.UpdateSubOrganizationMemberRoleWithHttpInfo(orgId, suborgId, userId, updateMemberRoleRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateSubOrganizationMemberRoleWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **suborgId** | **string** |  |  |
| **userId** | **string** |  |  |
| **updateMemberRoleRequest** | [**UpdateMemberRoleRequest**](UpdateMemberRoleRequest.md) |  |  |

### Return type

[**UpdateMemberRole200Response**](UpdateMemberRole200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Role updated |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updateuseraccountstatus"></a>
# **UpdateUserAccountStatus**
> UpdateUserAccountStatus200Response UpdateUserAccountStatus (string orgId, string userId, UpdateUserAccountStatusRequest updateUserAccountStatusRequest)

Update user account status (activate or suspend)

Set a user's account status to active or suspended. Used to approve pending users or suspend/activate accounts. Cannot change status of an organization owner. Requires owner or admin role. 

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
    public class UpdateUserAccountStatusExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var userId = "userId_example";  // string | 
            var updateUserAccountStatusRequest = new UpdateUserAccountStatusRequest(); // UpdateUserAccountStatusRequest | 

            try
            {
                // Update user account status (activate or suspend)
                UpdateUserAccountStatus200Response result = apiInstance.UpdateUserAccountStatus(orgId, userId, updateUserAccountStatusRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.UpdateUserAccountStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateUserAccountStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update user account status (activate or suspend)
    ApiResponse<UpdateUserAccountStatus200Response> response = apiInstance.UpdateUserAccountStatusWithHttpInfo(orgId, userId, updateUserAccountStatusRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.UpdateUserAccountStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **userId** | **string** |  |  |
| **updateUserAccountStatusRequest** | [**UpdateUserAccountStatusRequest**](UpdateUserAccountStatusRequest.md) |  |  |

### Return type

[**UpdateUserAccountStatus200Response**](UpdateUserAccountStatus200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User status updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="verifyorgcustomdomaindns"></a>
# **VerifyOrgCustomDomainDns**
> OrgVerifyCustomDomainDnsSuccessResponse VerifyOrgCustomDomainDns (string orgId, string projectId, string hostname)

Verify domain ownership via DNS TXT

Looks up TXT at `_mudbase-verify.<hostname>` for value `mudbase-domain-verification=<token>`.  When the server has **`CLOUDFLARE_API_TOKEN`** and **`CLOUDFLARE_ZONE_ID`** configured (and Fly ACME is **not** enabled), a successful verify also creates or refreshes a Cloudflare Custom Hostname (SSL for SaaS) and returns **`cloudflare`** with DCV hints.  When **Fly ACME** is enabled (**`FLY_API_TOKEN`** + **`CUSTOM_DOMAIN_FLY_ACME_ENABLED=true`** + app slug), a successful verify calls Fly’s Certificates API (`POST .../certificates/acme`) and persists DNS requirements. If Fly returns DNS rows and **`CUSTOM_DOMAIN_FLY_LEGACY_STAFF_PIPELINE`** is **not** set, status advances to **`cname_approved`** in the same response (no staff **`approve-cname`**); **`org.domain.cname_staff_queued`** is not logged for that path. Otherwise (legacy Fly or non-Fly), first success from `pending`/`failed` may move to **`cname_pending_staff`** and queue staff as before.  The **200** response may include **`dnsRecords`**, **`flyCertificateStatus`**, and **`routingCnameTarget`** from Fly’s **`dns_requirements.cname`** when provisioned.  Cloudflare SaaS and Fly ACME cannot both be enabled; the API process refuses to start if both are configured. 

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
    public class VerifyOrgCustomDomainDnsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // Configure Bearer token for authorization: OrgBearerAuth
            config.AccessToken = "YOUR_BEARER_TOKEN";

            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new OrganizationsApi(httpClient, config, httpClientHandler);
            var orgId = "orgId_example";  // string | 
            var projectId = "projectId_example";  // string | 
            var hostname = "hostname_example";  // string | 

            try
            {
                // Verify domain ownership via DNS TXT
                OrgVerifyCustomDomainDnsSuccessResponse result = apiInstance.VerifyOrgCustomDomainDns(orgId, projectId, hostname);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling OrganizationsApi.VerifyOrgCustomDomainDns: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the VerifyOrgCustomDomainDnsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Verify domain ownership via DNS TXT
    ApiResponse<OrgVerifyCustomDomainDnsSuccessResponse> response = apiInstance.VerifyOrgCustomDomainDnsWithHttpInfo(orgId, projectId, hostname);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling OrganizationsApi.VerifyOrgCustomDomainDnsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **orgId** | **string** |  |  |
| **projectId** | **string** |  |  |
| **hostname** | **string** |  |  |

### Return type

[**OrgVerifyCustomDomainDnsSuccessResponse**](OrgVerifyCustomDomainDnsSuccessResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | TXT verified. Fly ACME (default automation): often &#x60;cname_approved&#x60; when Fly returns DNS requirements; legacy Fly or non-Fly may show &#x60;cname_pending_staff&#x60; or &#x60;dns_verified&#x60;. Includes &#x60;dnsTxtHost&#x60;/&#x60;dnsTxtValue&#x60;, optional &#x60;cloudflare&#x60; (Cloudflare SaaS), optional &#x60;dnsRecords&#x60; + &#x60;flyCertificateStatus&#x60; when Fly ACME ran after this verify. |  -  |
| **400** | dns_verification_failed (TXT missing or wrong); body includes dnsTxtHost, dnsTxtValue, challengeHost, expectedTxt |  -  |
| **503** | dns_lookup_error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

