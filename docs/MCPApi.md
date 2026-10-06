# Mudbase.SDK.Api.MCPApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**McpConfigGet**](MCPApi.md#mcpconfigget) | **GET** /mcp/config | MCP connection status for the current org |

<a id="mcpconfigget"></a>
# **McpConfigGet**
> McpConfigGet200Response McpConfigGet ()

MCP connection status for the current org

Whether the org's plan includes MCP access and, when enabled, the endpoint URL an MCP client should connect to (the org's dedicated API host if it has dedicated infrastructure, otherwise the shared platform host). Auth here is the normal dashboard session - this powers the console's MCP settings page, distinct from the API-key-authenticated POST / endpoint an actual MCP client calls.

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
    public class McpConfigGetExample
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
            var apiInstance = new MCPApi(httpClient, config, httpClientHandler);

            try
            {
                // MCP connection status for the current org
                McpConfigGet200Response result = apiInstance.McpConfigGet();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling MCPApi.McpConfigGet: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the McpConfigGetWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // MCP connection status for the current org
    ApiResponse<McpConfigGet200Response> response = apiInstance.McpConfigGetWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling MCPApi.McpConfigGetWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**McpConfigGet200Response**](McpConfigGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | MCP status for the current org |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

