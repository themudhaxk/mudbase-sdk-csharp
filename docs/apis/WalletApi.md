# Mudbase.SDK.Api.WalletApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**WalletBroadcastTransaction**](WalletApi.md#walletbroadcasttransaction) | **POST** /api/wallet/non-custodial/broadcast | Broadcast a client-signed transaction |
| [**WalletCreateWebhook**](WalletApi.md#walletcreatewebhook) | **POST** /api/wallet/non-custodial/webhooks | Create a wallet webhook |
| [**WalletDeleteAddress**](WalletApi.md#walletdeleteaddress) | **DELETE** /api/wallet/non-custodial/addresses/{addressId} | Delete (soft-delete) a non-custodial address |
| [**WalletDeleteWebhook**](WalletApi.md#walletdeletewebhook) | **DELETE** /api/wallet/non-custodial/webhooks/{webhookId} | Delete a wallet webhook |
| [**WalletEstimateGas**](WalletApi.md#walletestimategas) | **POST** /api/wallet/non-custodial/estimate-gas | Estimate network fee from blockchain (all supported chains; not controlled by Mudbase) |
| [**WalletGetAddress**](WalletApi.md#walletgetaddress) | **GET** /api/wallet/non-custodial/addresses/{addressId} | Get non-custodial address by ID |
| [**WalletGetBalance**](WalletApi.md#walletgetbalance) | **GET** /api/wallet/non-custodial/addresses/{addressId}/balance | Get balance for a non-custodial address |
| [**WalletGetCancelParams**](WalletApi.md#walletgetcancelparams) | **POST** /api/wallet/non-custodial/cancel | Get replacement tx params for cancel (stuck EVM tx) |
| [**WalletGetSpeedUpParams**](WalletApi.md#walletgetspeedupparams) | **POST** /api/wallet/non-custodial/speed-up | Get replacement tx params for speed-up (stuck EVM tx) |
| [**WalletGetTransactionByHash**](WalletApi.md#walletgettransactionbyhash) | **GET** /api/wallet/non-custodial/transactions/{txHash} | Get transaction by hash |
| [**WalletGetTransactions**](WalletApi.md#walletgettransactions) | **GET** /api/wallet/non-custodial/addresses/{addressId}/transactions | Get transaction history for a non-custodial address |
| [**WalletGetWebhookLogs**](WalletApi.md#walletgetwebhooklogs) | **GET** /api/wallet/non-custodial/webhooks/{webhookId}/logs | Get webhook delivery logs |
| [**WalletListAddresses**](WalletApi.md#walletlistaddresses) | **GET** /api/wallet/non-custodial/addresses | List registered non-custodial addresses |
| [**WalletListWebhooks**](WalletApi.md#walletlistwebhooks) | **GET** /api/wallet/non-custodial/webhooks | List wallet webhooks |
| [**WalletRegisterAddress**](WalletApi.md#walletregisteraddress) | **POST** /api/wallet/non-custodial/register-address | Register a non-custodial wallet address |
| [**WalletTestWebhook**](WalletApi.md#wallettestwebhook) | **POST** /api/wallet/non-custodial/webhooks/test | Test a webhook delivery (sends a single test payload) |
| [**WalletUpdateWebhook**](WalletApi.md#walletupdatewebhook) | **PUT** /api/wallet/non-custodial/webhooks/{webhookId} | Update a wallet webhook |

<a id="walletbroadcasttransaction"></a>
# **WalletBroadcastTransaction**
> WalletBroadcastTransaction200Response WalletBroadcastTransaction (WalletBroadcastTransactionRequest walletBroadcastTransactionRequest)

Broadcast a client-signed transaction

Broadcast a transaction that has been signed client-side. The transaction must be fully signed before sending. The fromAddress must be registered and belong to your organization (POST /api/wallet/non-custodial/register-address). **Supported chains:** EVM (ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo), UTXO (bitcoin, litecoin, dogecoin), and chain-specific (tron, solana, ton, cardano). Use `binance` or `bsc` for BNB Smart Chain. **Testing with custodial:** You can create a wallet via POST /api/wallet/create, get its private key via GET /api/wallet/{walletId}/private-key, register that address with POST /api/wallet/non-custodial/register-address, then build a signed tx (using POST /api/wallet/estimate-network-fee or estimate-gas for fees) and broadcast it here to test the non-custodial flow end-to-end. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletBroadcastTransactionRequest** | [**WalletBroadcastTransactionRequest**](WalletBroadcastTransactionRequest.md) | Chain, signed transaction (hex), and fromAddress (must be registered). |  |

### Return type

[**WalletBroadcastTransaction200Response**](WalletBroadcastTransaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction broadcast successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletcreatewebhook"></a>
# **WalletCreateWebhook**
> WalletCreateWebhook201Response WalletCreateWebhook (WalletCreateWebhookRequest walletCreateWebhookRequest)

Create a wallet webhook

Register a webhook URL to receive wallet events (balance updates, transaction confirmed/failed/detected/broadcast, token balance, address created/deactivated). Optional filters by addresses and chains. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletCreateWebhookRequest** | [**WalletCreateWebhookRequest**](WalletCreateWebhookRequest.md) | Webhook URL, events array, optional secret and filters (addresses, chains, projectId). |  |

### Return type

[**WalletCreateWebhook201Response**](WalletCreateWebhook201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Webhook created successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletdeleteaddress"></a>
# **WalletDeleteAddress**
> FunctionsDelete200Response WalletDeleteAddress (string addressId)

Delete (soft-delete) a non-custodial address

Soft-deletes a registered non-custodial address. The address is marked inactive and no longer used for broadcasts or balance/transaction queries. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** | Registered address ID to delete. |  |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletdeletewebhook"></a>
# **WalletDeleteWebhook**
> FunctionsDelete200Response WalletDeleteWebhook (string webhookId)

Delete a wallet webhook

Permanently delete a wallet webhook. Delivery will stop immediately.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** | Webhook ID (MongoDB ObjectId) to delete. |  |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook deleted successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletestimategas"></a>
# **WalletEstimateGas**
> WalletEstimateGas200Response WalletEstimateGas (WalletEstimateGasRequest walletEstimateGasRequest)

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require `transaction` (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only `chain` is required; `transaction` is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletEstimateGasRequest** | [**WalletEstimateGasRequest**](WalletEstimateGasRequest.md) | Chain and optional transaction shape (required for EVM). Returns network fee from blockchain. |  |

### Return type

[**WalletEstimateGas200Response**](WalletEstimateGas200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Network fee from blockchain RPC (not from Mudbase logic) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgetaddress"></a>
# **WalletGetAddress**
> NonCustodialAddressResponse WalletGetAddress (string addressId)

Get non-custodial address by ID

Returns metadata and status for a single registered non-custodial address (ID, address, chain, label, org, project, derivationPath, isActive, timestamps). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** | Registered address ID (MongoDB ObjectId). |  |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgetbalance"></a>
# **WalletGetBalance**
> WalletGetBalance200Response WalletGetBalance (string addressId)

Get balance for a non-custodial address

Returns native token balance (confirmed, unconfirmed, total, currency) for a registered non-custodial address. Updated periodically from the chain. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** | Registered address ID. |  |

### Return type

[**WalletGetBalance200Response**](WalletGetBalance200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Balance information |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgetcancelparams"></a>
# **WalletGetCancelParams**
> WalletGetCancelParams200Response WalletGetCancelParams (WalletGetCancelParamsRequest walletGetCancelParamsRequest)

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to=self, value=0, data=0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletGetCancelParamsRequest** | [**WalletGetCancelParamsRequest**](WalletGetCancelParamsRequest.md) | Stuck transaction identifier (txId or txHash) and EVM chain for cancel. |  |

### Return type

[**WalletGetCancelParams200Response**](WalletGetCancelParams200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Cancel tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgetspeedupparams"></a>
# **WalletGetSpeedUpParams**
> WalletGetSpeedUpParams200Response WalletGetSpeedUpParams (WalletGetSpeedUpParamsRequest walletGetSpeedUpParamsRequest)

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending >5 min (stuck). EVM chains only. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletGetSpeedUpParamsRequest** | [**WalletGetSpeedUpParamsRequest**](WalletGetSpeedUpParamsRequest.md) | Stuck transaction identifier (txId or txHash) and EVM chain. |  |

### Return type

[**WalletGetSpeedUpParams200Response**](WalletGetSpeedUpParams200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Replacement tx params (client signs and broadcasts via /broadcast) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgettransactionbyhash"></a>
# **WalletGetTransactionByHash**
> WalletGetTransactionByHash200Response WalletGetTransactionByHash (string txHash, string chain)

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **txHash** | **string** | Transaction hash (e.g. 0x... for EVM, or block explorer format for UTXO) |  |
| **chain** | **string** | Chain the transaction belongs to (required for lookup) |  |

### Return type

[**WalletGetTransactionByHash200Response**](WalletGetTransactionByHash200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction details |  -  |
| **400** | Bad Request - missing or invalid chain (add ?chain&#x3D;ethereum) |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgettransactions"></a>
# **WalletGetTransactions**
> WalletGetTransactions200Response WalletGetTransactions (string addressId, int limit = null, int page = null)

Get transaction history for a non-custodial address

Returns paginated transaction history for a registered non-custodial address (incoming/outgoing, status, confirmations, amounts). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** | Registered address ID. |  |
| **limit** | **int** | Number of transactions per page. | [optional] [default to 50] |
| **page** | **int** | Page number (1-based). | [optional] [default to 1] |

### Return type

[**WalletGetTransactions200Response**](WalletGetTransactions200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Transaction history |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Resource not found. The **error** field contains the exact backend message, e.g. \&quot;File not found\&quot;, \&quot;Project not found\&quot;, \&quot;User not found\&quot;, \&quot;Project not found or access denied\&quot;, \&quot;Webhook not found\&quot;, \&quot;Organization not found\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletgetwebhooklogs"></a>
# **WalletGetWebhookLogs**
> WalletGetWebhookLogs200Response WalletGetWebhookLogs (string webhookId, int limit = null)

Get webhook delivery logs

List delivery attempts for a wallet webhook (success/failure, payload, response, duration). Paginated by limit.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** | Webhook ID (MongoDB ObjectId) to get logs for. |  |
| **limit** | **int** | Maximum number of log entries to return. | [optional] [default to 50] |

### Return type

[**WalletGetWebhookLogs200Response**](WalletGetWebhookLogs200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook delivery logs |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletlistaddresses"></a>
# **WalletListAddresses**
> WalletListAddresses200Response WalletListAddresses (string chain = null, string projectId = null)

List registered non-custodial addresses

Returns all non-custodial addresses registered for the current project/organization. Optional filters by chain and projectId. Addresses must be registered via POST /api/wallet/non-custodial/register-address before use. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **chain** | **string** | Filter by chain (optional) | [optional]  |
| **projectId** | **string** | Filter by project ID (optional). | [optional]  |

### Return type

[**WalletListAddresses200Response**](WalletListAddresses200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of registered addresses |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletlistwebhooks"></a>
# **WalletListWebhooks**
> WalletListWebhooks200Response WalletListWebhooks (string projectId = null)

List wallet webhooks

Returns all wallet webhooks for the current context, optionally filtered by projectId. Includes delivery stats and active status. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Filter by project ID (optional). | [optional]  |

### Return type

[**WalletListWebhooks200Response**](WalletListWebhooks200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | List of webhooks |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletregisteraddress"></a>
# **WalletRegisterAddress**
> NonCustodialAddressResponse WalletRegisterAddress (WalletRegisterAddressRequest walletRegisterAddressRequest)

Register a non-custodial wallet address

Register a public wallet address for balance monitoring, transaction indexing, and webhook notifications. Keys are never sent to the server; generation and signing happen client-side only. Supports EVM, UTXO, Solana, Tron, TON, Cardano, and other chains. Optionally provide derivation path and label for multi-address tracking. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletRegisterAddressRequest** | [**WalletRegisterAddressRequest**](WalletRegisterAddressRequest.md) | Public address, chain identifier, and optional derivation path and label. projectId scopes the registration to a project. |  |

### Return type

[**NonCustodialAddressResponse**](NonCustodialAddressResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Address registered successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="wallettestwebhook"></a>
# **WalletTestWebhook**
> WalletTestWebhook200Response WalletTestWebhook (WalletTestWebhookRequest walletTestWebhookRequest)

Test a webhook delivery (sends a single test payload)

Sends a test payload to the given URL to verify webhook connectivity and signature. Uses the same signing as real deliveries.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletTestWebhookRequest** | [**WalletTestWebhookRequest**](WalletTestWebhookRequest.md) | URL to send the test POST to; optional secret and projectId for scoping; optional event type to simulate. |  |

### Return type

[**WalletTestWebhook200Response**](WalletTestWebhook200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Test result |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="walletupdatewebhook"></a>
# **WalletUpdateWebhook**
> WalletUpdateWebhook200Response WalletUpdateWebhook (string webhookId, WalletUpdateWebhookRequest walletUpdateWebhookRequest)

Update a wallet webhook

Update webhook URL, events, secret, or filters. Partially applied; only provided fields are updated.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** | Webhook ID (MongoDB ObjectId) to update. |  |
| **walletUpdateWebhookRequest** | [**WalletUpdateWebhookRequest**](WalletUpdateWebhookRequest.md) | Fields to update (url, events, secret, filters). Omitted fields are left unchanged. |  |

### Return type

[**WalletUpdateWebhook200Response**](WalletUpdateWebhook200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook updated successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Webhook not found (exact backend message for webhook endpoints). |  -  |
| **429** | Rate limit exceeded. The **error** field contains the exact backend message, e.g. \&quot;API key rate limit exceeded\&quot;, \&quot;Please wait before requesting another magic link\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

