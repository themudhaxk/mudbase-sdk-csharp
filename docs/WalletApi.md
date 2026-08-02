# Mudbase.SDK.Api.WalletApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**BroadcastNonCustodialTransaction**](WalletApi.md#broadcastnoncustodialtransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**CalculateWalletFee**](WalletApi.md#calculatewalletfee) | **POST** /api/wallet/calculate-fee | Get network fee only (alias for POST /api/wallet/estimate-network-fee) |
| [**CreateWallet**](WalletApi.md#createwallet) | **POST** /api/wallet/create | Create new wallet (for testing non-custodial) |
| [**CreateWalletWebhook**](WalletApi.md#createwalletwebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**DeleteNonCustodialAddress**](WalletApi.md#deletenoncustodialaddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete or deactivate a monitored wallet address |
| [**DeleteWalletWebhook**](WalletApi.md#deletewalletwebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**EstimateNetworkFee**](WalletApi.md#estimatenetworkfee) | **POST** /api/wallet/estimate-network-fee | Estimate network fee (preferred; reads from fee oracle cache) |
| [**EstimateNonCustodialGas**](WalletApi.md#estimatenoncustodialgas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**GeneratePrivateKey**](WalletApi.md#generateprivatekey) | **POST** /api/wallet/generate-key | Generate private key |
| [**GetAllFees**](WalletApi.md#getallfees) | **GET** /api/wallet/fees | Get all chain network fees (fee oracle snapshot) |
| [**GetBalance**](WalletApi.md#getbalance) | **GET** /api/wallet/{walletId}/balance | Get wallet balance |
| [**GetCancelParams**](WalletApi.md#getcancelparams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**GetNetworkStatus**](WalletApi.md#getnetworkstatus) | **GET** /api/wallet/network-status | Get network status (congestion + fee metric per chain) |
| [**GetNonCustodialAddress**](WalletApi.md#getnoncustodialaddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**GetNonCustodialBalance**](WalletApi.md#getnoncustodialbalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**GetNonCustodialTransactionByHash**](WalletApi.md#getnoncustodialtransactionbyhash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**GetNonCustodialTransactions**](WalletApi.md#getnoncustodialtransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**GetSpeedUpParams**](WalletApi.md#getspeedupparams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**GetSupportedCurrencies**](WalletApi.md#getsupportedcurrencies) | **GET** /api/wallet/currencies | Get supported currencies and chains |
| [**GetTransaction**](WalletApi.md#gettransaction) | **GET** /api/wallet/transactions/{transactionId} | Get transaction details |
| [**GetTransactionHistory**](WalletApi.md#gettransactionhistory) | **GET** /api/wallet/transactions | Get transaction history (custodial wallets; same monitoring as non-custodial) |
| [**GetUserWallets**](WalletApi.md#getuserwallets) | **GET** /api/wallet | Get user wallets |
| [**GetWalletFeeConfig**](WalletApi.md#getwalletfeeconfig) | **GET** /api/wallet/projects/{projectId}/fee-config | Get project fee configuration (for non-custodial / external users) |
| [**GetWalletPrivateKey**](WalletApi.md#getwalletprivatekey) | **GET** /api/wallet/{walletId}/private-key | Get wallet private key (WARNING: Sensitive data; for testing non-custodial) |
| [**GetWalletWebhookLogs**](WalletApi.md#getwalletwebhooklogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**ListNonCustodialAddresses**](WalletApi.md#listnoncustodialaddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**ListWalletWebhooks**](WalletApi.md#listwalletwebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**RegisterNonCustodialAddress**](WalletApi.md#registernoncustodialaddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**TestWalletWebhook**](WalletApi.md#testwalletwebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**UpdateNonCustodialAddress**](WalletApi.md#updatenoncustodialaddress) | **PUT** /api/wallet/non-custodial/addresses/{addressId} | Update a monitored wallet address |
| [**UpdateWalletFeeConfig**](WalletApi.md#updatewalletfeeconfig) | **PATCH** /api/wallet/projects/{projectId}/fee-config | Update project fee configuration (for non-custodial / external users) |
| [**UpdateWalletWebhook**](WalletApi.md#updatewalletwebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |
| [**ValidateAddress**](WalletApi.md#validateaddress) | **POST** /api/wallet/validate-address | Validate cryptocurrency address |
| [**Withdraw**](WalletApi.md#withdraw) | **POST** /api/wallet/{walletId}/withdraw | Prepare withdrawal (semi-transaction; broadcast via non-custodial) |

<a id="broadcastnoncustodialtransaction"></a>
# **BroadcastNonCustodialTransaction**
> BroadcastNonCustodialTransaction200Response BroadcastNonCustodialTransaction (BroadcastNonCustodialTransactionRequest broadcastNonCustodialTransactionRequest)

Broadcast a client-signed transaction

Broadcast a transaction that has been signed client-side. The transaction must be fully signed before sending. The fromAddress must be registered and belong to your organization (POST /api/wallet/non-custodial/register-address). **Supported chains:** EVM (ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo), UTXO (bitcoin, litecoin, dogecoin), and chain-specific (tron, solana, ton, cardano). Use `binance` or `bsc` for BNB Smart Chain. **Testing with custodial:** You can create a wallet via POST /api/wallet/create, get its private key via GET /api/wallet/{walletId}/private-key, register that address with POST /api/wallet/non-custodial/register-address, then build a signed tx (using POST /api/wallet/estimate-network-fee or estimate-gas for fees) and broadcast it here to test the non-custodial flow end-to-end. 

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
    public class BroadcastNonCustodialTransactionExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var broadcastNonCustodialTransactionRequest = new BroadcastNonCustodialTransactionRequest(); // BroadcastNonCustodialTransactionRequest | 

            try
            {
                // Broadcast a client-signed transaction
                BroadcastNonCustodialTransaction200Response result = apiInstance.BroadcastNonCustodialTransaction(broadcastNonCustodialTransactionRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.BroadcastNonCustodialTransaction: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the BroadcastNonCustodialTransactionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Broadcast a client-signed transaction
    ApiResponse<BroadcastNonCustodialTransaction200Response> response = apiInstance.BroadcastNonCustodialTransactionWithHttpInfo(broadcastNonCustodialTransactionRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.BroadcastNonCustodialTransactionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **broadcastNonCustodialTransactionRequest** | [**BroadcastNonCustodialTransactionRequest**](BroadcastNonCustodialTransactionRequest.md) |  |  |

### Return type

[**BroadcastNonCustodialTransaction200Response**](BroadcastNonCustodialTransaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction broadcast successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="calculatewalletfee"></a>
# **CalculateWalletFee**
> CalculateWalletFee200Response CalculateWalletFee (EstimateNetworkFeeRequest estimateNetworkFeeRequest, string? fresh = null)

Get network fee only (alias for POST /api/wallet/estimate-network-fee)

Returns **network fee only**, estimated from the blockchain (RPC / fee APIs). No platform fee or project fee. **Same as POST /api/wallet/estimate-network-fee.** Prefer estimate-network-fee for clarity. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). Use `?fresh=1` or header `X-Fee-Fresh: true` for a fresh estimate (bypass cache) right before building the transaction for broadcast. 

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
    public class CalculateWalletFeeExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var estimateNetworkFeeRequest = new EstimateNetworkFeeRequest(); // EstimateNetworkFeeRequest | 
            var fresh = "1";  // string? | Bypass cache and fetch current fee (use right before building tx for broadcast) (optional) 

            try
            {
                // Get network fee only (alias for POST /api/wallet/estimate-network-fee)
                CalculateWalletFee200Response result = apiInstance.CalculateWalletFee(estimateNetworkFeeRequest, fresh);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.CalculateWalletFee: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CalculateWalletFeeWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get network fee only (alias for POST /api/wallet/estimate-network-fee)
    ApiResponse<CalculateWalletFee200Response> response = apiInstance.CalculateWalletFeeWithHttpInfo(estimateNetworkFeeRequest, fresh);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.CalculateWalletFeeWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md) |  |  |
| **fresh** | **string?** | Bypass cache and fetch current fee (use right before building tx for broadcast) | [optional]  |

### Return type

[**CalculateWalletFee200Response**](CalculateWalletFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee only (from blockchain). No platform or project fee. |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createwallet"></a>
# **CreateWallet**
> CreateWallet201Response CreateWallet (CreateWalletRequest createWalletRequest)

Create new wallet (for testing non-custodial)

Create a custodial wallet. **Custodial is not used in production.** Use this to **test non-custodial flows**: create a wallet, get its private key (GET /api/wallet/{walletId}/private-key), register the same address with POST /api/wallet/non-custodial/register-address, then use estimate-network-fee and POST /api/wallet/non-custodial/broadcast to build and send a signed transaction. Transaction monitoring (pending/confirmed) applies to both custodial and non-custodial WalletTransaction records. 

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
    public class CreateWalletExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var createWalletRequest = new CreateWalletRequest(); // CreateWalletRequest | 

            try
            {
                // Create new wallet (for testing non-custodial)
                CreateWallet201Response result = apiInstance.CreateWallet(createWalletRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.CreateWallet: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateWalletWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create new wallet (for testing non-custodial)
    ApiResponse<CreateWallet201Response> response = apiInstance.CreateWalletWithHttpInfo(createWalletRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.CreateWalletWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createWalletRequest** | [**CreateWalletRequest**](CreateWalletRequest.md) |  |  |

### Return type

[**CreateWallet201Response**](CreateWallet201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Wallet created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createwalletwebhook"></a>
# **CreateWalletWebhook**
> CreateWalletWebhook201Response CreateWalletWebhook (CreateWalletWebhookRequest createWalletWebhookRequest)

Create a wallet webhook

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
    public class CreateWalletWebhookExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var createWalletWebhookRequest = new CreateWalletWebhookRequest(); // CreateWalletWebhookRequest | 

            try
            {
                // Create a wallet webhook
                CreateWalletWebhook201Response result = apiInstance.CreateWalletWebhook(createWalletWebhookRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.CreateWalletWebhook: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateWalletWebhookWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a wallet webhook
    ApiResponse<CreateWalletWebhook201Response> response = apiInstance.CreateWalletWebhookWithHttpInfo(createWalletWebhookRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.CreateWalletWebhookWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **createWalletWebhookRequest** | [**CreateWalletWebhookRequest**](CreateWalletWebhookRequest.md) |  |  |

### Return type

[**CreateWalletWebhook201Response**](CreateWalletWebhook201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Webhook created successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletenoncustodialaddress"></a>
# **DeleteNonCustodialAddress**
> DeleteFunction200Response DeleteNonCustodialAddress (string addressId, bool? permanent = null)

Delete or deactivate a monitored wallet address

**Soft delete (default):** Omit **permanent** or set to false. The address is deactivated (isActive = false); it no longer appears in list or receives monitoring but the record remains for audit. **Permanent delete:** Set query **permanent=true** to remove the address record from the database. Use when you need to fully remove the monitored address. 

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
    public class DeleteNonCustodialAddressExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var addressId = "addressId_example";  // string | 
            var permanent = false;  // bool? | If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete) (optional)  (default to false)

            try
            {
                // Delete or deactivate a monitored wallet address
                DeleteFunction200Response result = apiInstance.DeleteNonCustodialAddress(addressId, permanent);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.DeleteNonCustodialAddress: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteNonCustodialAddressWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete or deactivate a monitored wallet address
    ApiResponse<DeleteFunction200Response> response = apiInstance.DeleteNonCustodialAddressWithHttpInfo(addressId, permanent);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.DeleteNonCustodialAddressWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **permanent** | **bool?** | If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete) | [optional] [default to false] |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address deactivated or permanently deleted |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletewalletwebhook"></a>
# **DeleteWalletWebhook**
> DeleteFunction200Response DeleteWalletWebhook (string webhookId)

Delete a wallet webhook

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
    public class DeleteWalletWebhookExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var webhookId = "webhookId_example";  // string | 

            try
            {
                // Delete a wallet webhook
                DeleteFunction200Response result = apiInstance.DeleteWalletWebhook(webhookId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.DeleteWalletWebhook: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteWalletWebhookWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a wallet webhook
    ApiResponse<DeleteFunction200Response> response = apiInstance.DeleteWalletWebhookWithHttpInfo(webhookId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.DeleteWalletWebhookWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** |  |  |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook deleted successfully |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="estimatenetworkfee"></a>
# **EstimateNetworkFee**
> EstimateNetworkFee200Response EstimateNetworkFee (EstimateNetworkFeeRequest estimateNetworkFeeRequest, string? fresh = null)

Estimate network fee (preferred; reads from fee oracle cache)

Returns **network fee only** from the blockchain. **Preferred endpoint** for network fee. Uses a fee oracle: fees are polled every 15–20s and cached, so responses are fast and RPC load is minimal (same strategy as large wallets). No platform fee. Request/response identical to POST /api/wallet/calculate-fee (which is an alias). See docs/FEE_ARCHITECTURE.md. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). **Fresh fee before broadcast:** To avoid stuck transactions, get a fresh estimate right before building/signing: use query `?fresh=1` or header `X-Fee-Fresh: true` to bypass cache. 

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
    public class EstimateNetworkFeeExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var estimateNetworkFeeRequest = new EstimateNetworkFeeRequest(); // EstimateNetworkFeeRequest | 
            var fresh = "1";  // string? | Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast) (optional) 

            try
            {
                // Estimate network fee (preferred; reads from fee oracle cache)
                EstimateNetworkFee200Response result = apiInstance.EstimateNetworkFee(estimateNetworkFeeRequest, fresh);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.EstimateNetworkFee: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the EstimateNetworkFeeWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Estimate network fee (preferred; reads from fee oracle cache)
    ApiResponse<EstimateNetworkFee200Response> response = apiInstance.EstimateNetworkFeeWithHttpInfo(estimateNetworkFeeRequest, fresh);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.EstimateNetworkFeeWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md) |  |  |
| **fresh** | **string?** | Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast) | [optional]  |

### Return type

[**EstimateNetworkFee200Response**](EstimateNetworkFee200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee only (from blockchain). No platform or project fee. |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="estimatenoncustodialgas"></a>
# **EstimateNonCustodialGas**
> EstimateNonCustodialGas200Response EstimateNonCustodialGas (EstimateNonCustodialGasRequest estimateNonCustodialGasRequest)

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require `transaction` (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only `chain` is required; `transaction` is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s. 

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
    public class EstimateNonCustodialGasExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var estimateNonCustodialGasRequest = new EstimateNonCustodialGasRequest(); // EstimateNonCustodialGasRequest | 

            try
            {
                // Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)
                EstimateNonCustodialGas200Response result = apiInstance.EstimateNonCustodialGas(estimateNonCustodialGasRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.EstimateNonCustodialGas: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the EstimateNonCustodialGasWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)
    ApiResponse<EstimateNonCustodialGas200Response> response = apiInstance.EstimateNonCustodialGasWithHttpInfo(estimateNonCustodialGasRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.EstimateNonCustodialGasWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **estimateNonCustodialGasRequest** | [**EstimateNonCustodialGasRequest**](EstimateNonCustodialGasRequest.md) |  |  |

### Return type

[**EstimateNonCustodialGas200Response**](EstimateNonCustodialGas200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee from blockchain RPC (not from Mudbase logic) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="generateprivatekey"></a>
# **GeneratePrivateKey**
> GeneratePrivateKey200Response GeneratePrivateKey (GeneratePrivateKeyRequest generatePrivateKeyRequest)

Generate private key

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
    public class GeneratePrivateKeyExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var generatePrivateKeyRequest = new GeneratePrivateKeyRequest(); // GeneratePrivateKeyRequest | 

            try
            {
                // Generate private key
                GeneratePrivateKey200Response result = apiInstance.GeneratePrivateKey(generatePrivateKeyRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GeneratePrivateKey: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GeneratePrivateKeyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Generate private key
    ApiResponse<GeneratePrivateKey200Response> response = apiInstance.GeneratePrivateKeyWithHttpInfo(generatePrivateKeyRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GeneratePrivateKeyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **generatePrivateKeyRequest** | [**GeneratePrivateKeyRequest**](GeneratePrivateKeyRequest.md) |  |  |

### Return type

[**GeneratePrivateKey200Response**](GeneratePrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Private key generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getallfees"></a>
# **GetAllFees**
> GetAllFees200Response GetAllFees ()

Get all chain network fees (fee oracle snapshot)

Returns **all chain network fees** in one call. Reads from the fee oracle cache (no RPC during the request). Each chain returns the **full fee object** (networkFee, gasPriceGwei, congestion, estimatedTime, feeTiers for EVM, etc.) for frontend/UX. Use for dashboards or \"current fees\" screens. 

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
    public class GetAllFeesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);

            try
            {
                // Get all chain network fees (fee oracle snapshot)
                GetAllFees200Response result = apiInstance.GetAllFees();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetAllFees: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetAllFeesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get all chain network fees (fee oracle snapshot)
    ApiResponse<GetAllFees200Response> response = apiInstance.GetAllFeesWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetAllFeesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**GetAllFees200Response**](GetAllFees200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee oracle snapshot (chain -&gt; full fee object) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getbalance"></a>
# **GetBalance**
> GetBalance200Response GetBalance (string walletId)

Get wallet balance

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
    public class GetBalanceExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var walletId = "walletId_example";  // string | 

            try
            {
                // Get wallet balance
                GetBalance200Response result = apiInstance.GetBalance(walletId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetBalance: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetBalanceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get wallet balance
    ApiResponse<GetBalance200Response> response = apiInstance.GetBalanceWithHttpInfo(walletId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetBalanceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletId** | **string** |  |  |

### Return type

[**GetBalance200Response**](GetBalance200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Wallet balance |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getcancelparams"></a>
# **GetCancelParams**
> GetCancelParams200Response GetCancelParams (GetCancelParamsRequest getCancelParamsRequest)

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to=self, value=0, data=0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only. 

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
    public class GetCancelParamsExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var getCancelParamsRequest = new GetCancelParamsRequest(); // GetCancelParamsRequest | 

            try
            {
                // Get replacement tx params for cancel (stuck EVM tx)
                GetCancelParams200Response result = apiInstance.GetCancelParams(getCancelParamsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetCancelParams: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetCancelParamsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get replacement tx params for cancel (stuck EVM tx)
    ApiResponse<GetCancelParams200Response> response = apiInstance.GetCancelParamsWithHttpInfo(getCancelParamsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetCancelParamsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **getCancelParamsRequest** | [**GetCancelParamsRequest**](GetCancelParamsRequest.md) |  |  |

### Return type

[**GetCancelParams200Response**](GetCancelParams200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cancel tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getnetworkstatus"></a>
# **GetNetworkStatus**
> GetNetworkStatus200Response GetNetworkStatus ()

Get network status (congestion + fee metric per chain)

Returns **network status** per chain (congestion and main fee metric). Use to show network health before sending transactions. Same data as GET /fees but trimmed to congestion + gasPriceGwei (EVM) or satPerVb (UTXO) and networkFee. 

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
    public class GetNetworkStatusExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);

            try
            {
                // Get network status (congestion + fee metric per chain)
                GetNetworkStatus200Response result = apiInstance.GetNetworkStatus();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetNetworkStatus: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetNetworkStatusWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get network status (congestion + fee metric per chain)
    ApiResponse<GetNetworkStatus200Response> response = apiInstance.GetNetworkStatusWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetNetworkStatusWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**GetNetworkStatus200Response**](GetNetworkStatus200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network status per chain |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getnoncustodialaddress"></a>
# **GetNonCustodialAddress**
> NonCustodialAddressResponse GetNonCustodialAddress (string addressId)

Get non-custodial address by ID

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
    public class GetNonCustodialAddressExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var addressId = "addressId_example";  // string | 

            try
            {
                // Get non-custodial address by ID
                NonCustodialAddressResponse result = apiInstance.GetNonCustodialAddress(addressId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetNonCustodialAddress: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetNonCustodialAddressWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get non-custodial address by ID
    ApiResponse<NonCustodialAddressResponse> response = apiInstance.GetNonCustodialAddressWithHttpInfo(addressId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetNonCustodialAddressWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getnoncustodialbalance"></a>
# **GetNonCustodialBalance**
> GetNonCustodialBalance200Response GetNonCustodialBalance (string addressId)

Get balance for a non-custodial address

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
    public class GetNonCustodialBalanceExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var addressId = "addressId_example";  // string | 

            try
            {
                // Get balance for a non-custodial address
                GetNonCustodialBalance200Response result = apiInstance.GetNonCustodialBalance(addressId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetNonCustodialBalance: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetNonCustodialBalanceWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get balance for a non-custodial address
    ApiResponse<GetNonCustodialBalance200Response> response = apiInstance.GetNonCustodialBalanceWithHttpInfo(addressId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetNonCustodialBalanceWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |

### Return type

[**GetNonCustodialBalance200Response**](GetNonCustodialBalance200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Balance information |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getnoncustodialtransactionbyhash"></a>
# **GetNonCustodialTransactionByHash**
> GetNonCustodialTransactionByHash200Response GetNonCustodialTransactionByHash (string txHash, string chain)

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains). 

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
    public class GetNonCustodialTransactionByHashExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var txHash = "txHash_example";  // string | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO)
            var chain = "ethereum";  // string | Chain the transaction belongs to (required for lookup)

            try
            {
                // Get transaction by hash
                GetNonCustodialTransactionByHash200Response result = apiInstance.GetNonCustodialTransactionByHash(txHash, chain);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetNonCustodialTransactionByHash: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetNonCustodialTransactionByHashWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get transaction by hash
    ApiResponse<GetNonCustodialTransactionByHash200Response> response = apiInstance.GetNonCustodialTransactionByHashWithHttpInfo(txHash, chain);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetNonCustodialTransactionByHashWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **txHash** | **string** | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO) |  |
| **chain** | **string** | Chain the transaction belongs to (required for lookup) |  |

### Return type

[**GetNonCustodialTransactionByHash200Response**](GetNonCustodialTransactionByHash200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **400** | Bad Request - missing or invalid chain (add ?chain&#x3D;ethereum) |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getnoncustodialtransactions"></a>
# **GetNonCustodialTransactions**
> GetNonCustodialTransactions200Response GetNonCustodialTransactions (string addressId, int? limit = null, int? page = null)

Get transaction history for a non-custodial address

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
    public class GetNonCustodialTransactionsExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var addressId = "addressId_example";  // string | 
            var limit = 50;  // int? |  (optional)  (default to 50)
            var page = 1;  // int? |  (optional)  (default to 1)

            try
            {
                // Get transaction history for a non-custodial address
                GetNonCustodialTransactions200Response result = apiInstance.GetNonCustodialTransactions(addressId, limit, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetNonCustodialTransactions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetNonCustodialTransactionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get transaction history for a non-custodial address
    ApiResponse<GetNonCustodialTransactions200Response> response = apiInstance.GetNonCustodialTransactionsWithHttpInfo(addressId, limit, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetNonCustodialTransactionsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **limit** | **int?** |  | [optional] [default to 50] |
| **page** | **int?** |  | [optional] [default to 1] |

### Return type

[**GetNonCustodialTransactions200Response**](GetNonCustodialTransactions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getspeedupparams"></a>
# **GetSpeedUpParams**
> GetSpeedUpParams200Response GetSpeedUpParams (GetSpeedUpParamsRequest getSpeedUpParamsRequest)

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending >5 min (stuck). EVM chains only. 

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
    public class GetSpeedUpParamsExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var getSpeedUpParamsRequest = new GetSpeedUpParamsRequest(); // GetSpeedUpParamsRequest | 

            try
            {
                // Get replacement tx params for speed-up (stuck EVM tx)
                GetSpeedUpParams200Response result = apiInstance.GetSpeedUpParams(getSpeedUpParamsRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetSpeedUpParams: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetSpeedUpParamsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get replacement tx params for speed-up (stuck EVM tx)
    ApiResponse<GetSpeedUpParams200Response> response = apiInstance.GetSpeedUpParamsWithHttpInfo(getSpeedUpParamsRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetSpeedUpParamsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **getSpeedUpParamsRequest** | [**GetSpeedUpParamsRequest**](GetSpeedUpParamsRequest.md) |  |  |

### Return type

[**GetSpeedUpParams200Response**](GetSpeedUpParams200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Replacement tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getsupportedcurrencies"></a>
# **GetSupportedCurrencies**
> GetSupportedCurrencies200Response GetSupportedCurrencies ()

Get supported currencies and chains

Returns the list of **platform-supported cryptocurrencies and chains** for non-custodial wallets, broadcast, and multi-chain use. Custodial wallet is no longer used in production; this endpoint is the source of truth for supported chains and currencies. **Supported:** BTC, LTC, DOGE, ETH, ETC, CELO, SOL, TRX, TON, Polygon (MATIC), Arbitrum, Optimism, Base, BSC/BNB, Avalanche (AVAX), Cardano (ADA), USDT. Each item includes **code** (currency symbol), **name** (display name), **chain** (chain id for API calls). USDT includes **networks** (ETH, BSC, TRX, SOL, POLYGON). Use **chain** with non-custodial endpoints (register-address, broadcast, estimate-gas). Use **code** for display and fee/currency selection. This is a public endpoint - no authentication required. 

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
    public class GetSupportedCurrenciesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "https://cloud.mudbase.dev";
            // create instances of HttpClient, HttpClientHandler to be reused later with different Api classes
            HttpClient httpClient = new HttpClient();
            HttpClientHandler httpClientHandler = new HttpClientHandler();
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);

            try
            {
                // Get supported currencies and chains
                GetSupportedCurrencies200Response result = apiInstance.GetSupportedCurrencies();
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetSupportedCurrencies: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetSupportedCurrenciesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get supported currencies and chains
    ApiResponse<GetSupportedCurrencies200Response> response = apiInstance.GetSupportedCurrenciesWithHttpInfo();
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetSupportedCurrenciesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters
This endpoint does not need any parameter.
### Return type

[**GetSupportedCurrencies200Response**](GetSupportedCurrencies200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Supported currencies and chains (currencies array and count) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gettransaction"></a>
# **GetTransaction**
> GetTransaction200Response GetTransaction (string transactionId)

Get transaction details

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
    public class GetTransactionExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var transactionId = "transactionId_example";  // string | 

            try
            {
                // Get transaction details
                GetTransaction200Response result = apiInstance.GetTransaction(transactionId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetTransaction: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTransactionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get transaction details
    ApiResponse<GetTransaction200Response> response = apiInstance.GetTransactionWithHttpInfo(transactionId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetTransactionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **transactionId** | **string** |  |  |

### Return type

[**GetTransaction200Response**](GetTransaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gettransactionhistory"></a>
# **GetTransactionHistory**
> GetTransactionHistory200Response GetTransactionHistory (string? walletId = null, int? limit = null, int? page = null)

Get transaction history (custodial wallets; same monitoring as non-custodial)

Returns transaction history for custodial wallets. Transactions are stored and monitored the same way as non-custodial (WalletTransaction); status updates (pending, broadcast, confirmed, failed) and stuck detection apply to both. 

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
    public class GetTransactionHistoryExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var walletId = "walletId_example";  // string? |  (optional) 
            var limit = 20;  // int? |  (optional)  (default to 20)
            var page = 1;  // int? |  (optional)  (default to 1)

            try
            {
                // Get transaction history (custodial wallets; same monitoring as non-custodial)
                GetTransactionHistory200Response result = apiInstance.GetTransactionHistory(walletId, limit, page);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetTransactionHistory: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTransactionHistoryWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get transaction history (custodial wallets; same monitoring as non-custodial)
    ApiResponse<GetTransactionHistory200Response> response = apiInstance.GetTransactionHistoryWithHttpInfo(walletId, limit, page);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetTransactionHistoryWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletId** | **string?** |  | [optional]  |
| **limit** | **int?** |  | [optional] [default to 20] |
| **page** | **int?** |  | [optional] [default to 1] |

### Return type

[**GetTransactionHistory200Response**](GetTransactionHistory200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getuserwallets"></a>
# **GetUserWallets**
> GetUserWallets200Response GetUserWallets (string? projectId = null, string? currency = null)

Get user wallets

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
    public class GetUserWalletsExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string? |  (optional) 
            var currency = "currency_example";  // string? |  (optional) 

            try
            {
                // Get user wallets
                GetUserWallets200Response result = apiInstance.GetUserWallets(projectId, currency);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetUserWallets: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetUserWalletsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get user wallets
    ApiResponse<GetUserWallets200Response> response = apiInstance.GetUserWalletsWithHttpInfo(projectId, currency);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetUserWalletsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string?** |  | [optional]  |
| **currency** | **string?** |  | [optional]  |

### Return type

[**GetUserWallets200Response**](GetUserWallets200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User wallets list (custodial; for testing) |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getwalletfeeconfig"></a>
# **GetWalletFeeConfig**
> GetWalletFeeConfig200Response GetWalletFeeConfig (string projectId)

Get project fee configuration (for non-custodial / external users)

Get project-level fee settings (enabled flag and fee percentage). **For non-custodial / external users** — e.g. when your app charges a fee on payouts or transfers. Custodial wallet is no longer used in production. Applies to all supported chains/currencies for that project. 

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
    public class GetWalletFeeConfigExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | Project ID

            try
            {
                // Get project fee configuration (for non-custodial / external users)
                GetWalletFeeConfig200Response result = apiInstance.GetWalletFeeConfig(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetWalletFeeConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetWalletFeeConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get project fee configuration (for non-custodial / external users)
    ApiResponse<GetWalletFeeConfig200Response> response = apiInstance.GetWalletFeeConfigWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetWalletFeeConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID |  |

### Return type

[**GetWalletFeeConfig200Response**](GetWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee configuration (applies to all supported currencies/chains for this project) |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getwalletprivatekey"></a>
# **GetWalletPrivateKey**
> GetWalletPrivateKey200Response GetWalletPrivateKey (string walletId)

Get wallet private key (WARNING: Sensitive data; for testing non-custodial)

Returns the wallet private key. **For testing non-custodial only:** use this key to sign a transaction locally, then register the wallet address via POST /api/wallet/non-custodial/register-address and broadcast the signed tx via POST /api/wallet/non-custodial/broadcast. 

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
    public class GetWalletPrivateKeyExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var walletId = "walletId_example";  // string | 

            try
            {
                // Get wallet private key (WARNING: Sensitive data; for testing non-custodial)
                GetWalletPrivateKey200Response result = apiInstance.GetWalletPrivateKey(walletId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetWalletPrivateKey: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetWalletPrivateKeyWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get wallet private key (WARNING: Sensitive data; for testing non-custodial)
    ApiResponse<GetWalletPrivateKey200Response> response = apiInstance.GetWalletPrivateKeyWithHttpInfo(walletId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetWalletPrivateKeyWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletId** | **string** |  |  |

### Return type

[**GetWalletPrivateKey200Response**](GetWalletPrivateKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Private key (shown only once) |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getwalletwebhooklogs"></a>
# **GetWalletWebhookLogs**
> GetWalletWebhookLogs200Response GetWalletWebhookLogs (string webhookId, int? limit = null)

Get webhook delivery logs

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
    public class GetWalletWebhookLogsExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var webhookId = "webhookId_example";  // string | 
            var limit = 50;  // int? |  (optional)  (default to 50)

            try
            {
                // Get webhook delivery logs
                GetWalletWebhookLogs200Response result = apiInstance.GetWalletWebhookLogs(webhookId, limit);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.GetWalletWebhookLogs: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetWalletWebhookLogsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get webhook delivery logs
    ApiResponse<GetWalletWebhookLogs200Response> response = apiInstance.GetWalletWebhookLogsWithHttpInfo(webhookId, limit);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.GetWalletWebhookLogsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** |  |  |
| **limit** | **int?** |  | [optional] [default to 50] |

### Return type

[**GetWalletWebhookLogs200Response**](GetWalletWebhookLogs200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listnoncustodialaddresses"></a>
# **ListNonCustodialAddresses**
> ListNonCustodialAddresses200Response ListNonCustodialAddresses (string? chain = null, string? projectId = null)

List registered non-custodial addresses

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
    public class ListNonCustodialAddressesExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var chain = "ethereum";  // string? | Filter by chain (optional) (optional) 
            var projectId = "projectId_example";  // string? |  (optional) 

            try
            {
                // List registered non-custodial addresses
                ListNonCustodialAddresses200Response result = apiInstance.ListNonCustodialAddresses(chain, projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.ListNonCustodialAddresses: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListNonCustodialAddressesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List registered non-custodial addresses
    ApiResponse<ListNonCustodialAddresses200Response> response = apiInstance.ListNonCustodialAddressesWithHttpInfo(chain, projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.ListNonCustodialAddressesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **chain** | **string?** | Filter by chain (optional) | [optional]  |
| **projectId** | **string?** |  | [optional]  |

### Return type

[**ListNonCustodialAddresses200Response**](ListNonCustodialAddresses200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of registered addresses |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listwalletwebhooks"></a>
# **ListWalletWebhooks**
> ListWalletWebhooks200Response ListWalletWebhooks (string? projectId = null)

List wallet webhooks

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
    public class ListWalletWebhooksExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string? |  (optional) 

            try
            {
                // List wallet webhooks
                ListWalletWebhooks200Response result = apiInstance.ListWalletWebhooks(projectId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.ListWalletWebhooks: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListWalletWebhooksWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List wallet webhooks
    ApiResponse<ListWalletWebhooks200Response> response = apiInstance.ListWalletWebhooksWithHttpInfo(projectId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.ListWalletWebhooksWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string?** |  | [optional]  |

### Return type

[**ListWalletWebhooks200Response**](ListWalletWebhooks200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of webhooks |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="registernoncustodialaddress"></a>
# **RegisterNonCustodialAddress**
> NonCustodialAddressResponse RegisterNonCustodialAddress (RegisterNonCustodialAddressRequest registerNonCustodialAddressRequest)

Register a non-custodial wallet address

Register a public wallet address for monitoring and indexing. All key operations (generation, signing) occur client-side only. 

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
    public class RegisterNonCustodialAddressExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var registerNonCustodialAddressRequest = new RegisterNonCustodialAddressRequest(); // RegisterNonCustodialAddressRequest | 

            try
            {
                // Register a non-custodial wallet address
                NonCustodialAddressResponse result = apiInstance.RegisterNonCustodialAddress(registerNonCustodialAddressRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.RegisterNonCustodialAddress: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the RegisterNonCustodialAddressWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Register a non-custodial wallet address
    ApiResponse<NonCustodialAddressResponse> response = apiInstance.RegisterNonCustodialAddressWithHttpInfo(registerNonCustodialAddressRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.RegisterNonCustodialAddressWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **registerNonCustodialAddressRequest** | [**RegisterNonCustodialAddressRequest**](RegisterNonCustodialAddressRequest.md) |  |  |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Address registered successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="testwalletwebhook"></a>
# **TestWalletWebhook**
> TestWalletWebhook200Response TestWalletWebhook (TestWalletWebhookRequest testWalletWebhookRequest)

Test a webhook delivery (sends a single test payload)

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
    public class TestWalletWebhookExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var testWalletWebhookRequest = new TestWalletWebhookRequest(); // TestWalletWebhookRequest | 

            try
            {
                // Test a webhook delivery (sends a single test payload)
                TestWalletWebhook200Response result = apiInstance.TestWalletWebhook(testWalletWebhookRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.TestWalletWebhook: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the TestWalletWebhookWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Test a webhook delivery (sends a single test payload)
    ApiResponse<TestWalletWebhook200Response> response = apiInstance.TestWalletWebhookWithHttpInfo(testWalletWebhookRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.TestWalletWebhookWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **testWalletWebhookRequest** | [**TestWalletWebhookRequest**](TestWalletWebhookRequest.md) |  |  |

### Return type

[**TestWalletWebhook200Response**](TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Test result |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatenoncustodialaddress"></a>
# **UpdateNonCustodialAddress**
> UpdateNonCustodialAddress200Response UpdateNonCustodialAddress (string addressId, UpdateNonCustodialAddressRequest? updateNonCustodialAddressRequest = null)

Update a monitored wallet address

Update metadata for a registered non-custodial address. Only **label** and **derivationPath** can be updated; address and chain are immutable. 

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
    public class UpdateNonCustodialAddressExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var addressId = "addressId_example";  // string | 
            var updateNonCustodialAddressRequest = new UpdateNonCustodialAddressRequest?(); // UpdateNonCustodialAddressRequest? |  (optional) 

            try
            {
                // Update a monitored wallet address
                UpdateNonCustodialAddress200Response result = apiInstance.UpdateNonCustodialAddress(addressId, updateNonCustodialAddressRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.UpdateNonCustodialAddress: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateNonCustodialAddressWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update a monitored wallet address
    ApiResponse<UpdateNonCustodialAddress200Response> response = apiInstance.UpdateNonCustodialAddressWithHttpInfo(addressId, updateNonCustodialAddressRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.UpdateNonCustodialAddressWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **updateNonCustodialAddressRequest** | [**UpdateNonCustodialAddressRequest?**](UpdateNonCustodialAddressRequest?.md) |  | [optional]  |

### Return type

[**UpdateNonCustodialAddress200Response**](UpdateNonCustodialAddress200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address updated successfully |  -  |
| **400** | Validation error (e.g. label too long, invalid derivation path) |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatewalletfeeconfig"></a>
# **UpdateWalletFeeConfig**
> UpdateWalletFeeConfig200Response UpdateWalletFeeConfig (string projectId, UpdateWalletFeeConfigRequest? updateWalletFeeConfigRequest = null)

Update project fee configuration (for non-custodial / external users)

Update project-level fee settings. **For non-custodial / external users** — e.g. fee charged on payouts or transfers. Custodial wallet is no longer used in production. Applies to **all supported currencies** (BTC, ETH, BNB, LTC, SOL, TRX, USDT). **feePercentage** is a decimal: use `0.01` for 1%, `0.005` for 0.5%, etc. (min 0, max 1). 

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
    public class UpdateWalletFeeConfigExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var projectId = "projectId_example";  // string | Project ID
            var updateWalletFeeConfigRequest = new UpdateWalletFeeConfigRequest?(); // UpdateWalletFeeConfigRequest? |  (optional) 

            try
            {
                // Update project fee configuration (for non-custodial / external users)
                UpdateWalletFeeConfig200Response result = apiInstance.UpdateWalletFeeConfig(projectId, updateWalletFeeConfigRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.UpdateWalletFeeConfig: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateWalletFeeConfigWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update project fee configuration (for non-custodial / external users)
    ApiResponse<UpdateWalletFeeConfig200Response> response = apiInstance.UpdateWalletFeeConfigWithHttpInfo(projectId, updateWalletFeeConfigRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.UpdateWalletFeeConfigWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID |  |
| **updateWalletFeeConfigRequest** | [**UpdateWalletFeeConfigRequest?**](UpdateWalletFeeConfigRequest?.md) |  | [optional]  |

### Return type

[**UpdateWalletFeeConfig200Response**](UpdateWalletFeeConfig200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee configuration updated |  -  |
| **400** | Bad request |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatewalletwebhook"></a>
# **UpdateWalletWebhook**
> UpdateWalletWebhook200Response UpdateWalletWebhook (string webhookId, UpdateWalletWebhookRequest updateWalletWebhookRequest)

Update a wallet webhook

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
    public class UpdateWalletWebhookExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var webhookId = "webhookId_example";  // string | 
            var updateWalletWebhookRequest = new UpdateWalletWebhookRequest(); // UpdateWalletWebhookRequest | 

            try
            {
                // Update a wallet webhook
                UpdateWalletWebhook200Response result = apiInstance.UpdateWalletWebhook(webhookId, updateWalletWebhookRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.UpdateWalletWebhook: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateWalletWebhookWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update a wallet webhook
    ApiResponse<UpdateWalletWebhook200Response> response = apiInstance.UpdateWalletWebhookWithHttpInfo(webhookId, updateWalletWebhookRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.UpdateWalletWebhookWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** |  |  |
| **updateWalletWebhookRequest** | [**UpdateWalletWebhookRequest**](UpdateWalletWebhookRequest.md) |  |  |

### Return type

[**UpdateWalletWebhook200Response**](UpdateWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook updated successfully |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="validateaddress"></a>
# **ValidateAddress**
> ValidateAddress200Response ValidateAddress (ValidateAddressRequest validateAddressRequest)

Validate cryptocurrency address

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
    public class ValidateAddressExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var validateAddressRequest = new ValidateAddressRequest(); // ValidateAddressRequest | 

            try
            {
                // Validate cryptocurrency address
                ValidateAddress200Response result = apiInstance.ValidateAddress(validateAddressRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.ValidateAddress: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ValidateAddressWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Validate cryptocurrency address
    ApiResponse<ValidateAddress200Response> response = apiInstance.ValidateAddressWithHttpInfo(validateAddressRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.ValidateAddressWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **validateAddressRequest** | [**ValidateAddressRequest**](ValidateAddressRequest.md) |  |  |

### Return type

[**ValidateAddress200Response**](ValidateAddress200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address validation result |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="withdraw"></a>
# **Withdraw**
> Withdraw200Response Withdraw (string walletId, WithdrawRequest withdrawRequest)

Prepare withdrawal (semi-transaction; broadcast via non-custodial)

**Semi-transaction:** Builds and signs the withdrawal but does **not** broadcast. Returns `signedTx`, `chain`, and `fromAddress` so the client can broadcast via POST /api/wallet/non-custodial/broadcast. The wallet address must be registered for your organization before broadcasting. Supports all platform chains/currencies (EVM, UTXO, Tron, Solana, USDT on ETH/BSC/TRX/SOL/POLYGON). Use for testing the non-custodial flow: create custodial wallet, get private key, register address, then call withdraw to get signed tx and broadcast it manually. 

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
    public class WithdrawExample
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
            var apiInstance = new WalletApi(httpClient, config, httpClientHandler);
            var walletId = "walletId_example";  // string | 
            var withdrawRequest = new WithdrawRequest(); // WithdrawRequest | 

            try
            {
                // Prepare withdrawal (semi-transaction; broadcast via non-custodial)
                Withdraw200Response result = apiInstance.Withdraw(walletId, withdrawRequest);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling WalletApi.Withdraw: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the WithdrawWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Prepare withdrawal (semi-transaction; broadcast via non-custodial)
    ApiResponse<Withdraw200Response> response = apiInstance.WithdrawWithHttpInfo(walletId, withdrawRequest);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling WalletApi.WithdrawWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletId** | **string** |  |  |
| **withdrawRequest** | [**WithdrawRequest**](WithdrawRequest.md) |  |  |

### Return type

[**Withdraw200Response**](Withdraw200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Semi-transaction ready; broadcast via POST /api/wallet/non-custodial/broadcast |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **500** | Internal server error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

