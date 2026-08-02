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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="calculatewalletfee"></a>
# **CalculateWalletFee**
> CalculateWalletFee200Response CalculateWalletFee (EstimateNetworkFeeRequest estimateNetworkFeeRequest, string fresh = null)

Get network fee only (alias for POST /api/wallet/estimate-network-fee)

Returns **network fee only**, estimated from the blockchain (RPC / fee APIs). No platform fee or project fee. **Same as POST /api/wallet/estimate-network-fee.** Prefer estimate-network-fee for clarity. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). Use `?fresh=1` or header `X-Fee-Fresh: true` for a fresh estimate (bypass cache) right before building the transaction for broadcast. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md) |  |  |
| **fresh** | **string** | Bypass cache and fetch current fee (use right before building tx for broadcast) | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createwallet"></a>
# **CreateWallet**
> CreateWallet201Response CreateWallet (CreateWalletRequest createWalletRequest)

Create new wallet (for testing non-custodial)

Create a custodial wallet. **Custodial is not used in production.** Use this to **test non-custodial flows**: create a wallet, get its private key (GET /api/wallet/{walletId}/private-key), register the same address with POST /api/wallet/non-custodial/register-address, then use estimate-network-fee and POST /api/wallet/non-custodial/broadcast to build and send a signed transaction. Transaction monitoring (pending/confirmed) applies to both custodial and non-custodial WalletTransaction records. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createwalletwebhook"></a>
# **CreateWalletWebhook**
> CreateWalletWebhook201Response CreateWalletWebhook (CreateWalletWebhookRequest createWalletWebhookRequest)

Create a wallet webhook


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletenoncustodialaddress"></a>
# **DeleteNonCustodialAddress**
> DeleteFunction200Response DeleteNonCustodialAddress (string addressId, bool permanent = null)

Delete or deactivate a monitored wallet address

**Soft delete (default):** Omit **permanent** or set to false. The address is deactivated (isActive = false); it no longer appears in list or receives monitoring but the record remains for audit. **Permanent delete:** Set query **permanent=true** to remove the address record from the database. Use when you need to fully remove the monitored address. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **permanent** | **bool** | If true, permanently delete the address from the database; if false or omitted, only deactivate (soft delete) | [optional] [default to false] |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletewalletwebhook"></a>
# **DeleteWalletWebhook**
> DeleteFunction200Response DeleteWalletWebhook (string webhookId)

Delete a wallet webhook


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="estimatenetworkfee"></a>
# **EstimateNetworkFee**
> EstimateNetworkFee200Response EstimateNetworkFee (EstimateNetworkFeeRequest estimateNetworkFeeRequest, string fresh = null)

Estimate network fee (preferred; reads from fee oracle cache)

Returns **network fee only** from the blockchain. **Preferred endpoint** for network fee. Uses a fee oracle: fees are polled every 15–20s and cached, so responses are fast and RPC load is minimal (same strategy as large wallets). No platform fee. Request/response identical to POST /api/wallet/calculate-fee (which is an alias). See docs/FEE_ARCHITECTURE.md. Supported currencies: BTC, ETH, BNB, LTC, SOL, TRX, USDT, MATIC, AVAX, CELO, DOGE, TON, ADA. For USDT, `network` is required (ETH, BSC, TRX, SOL, POLYGON). **Fresh fee before broadcast:** To avoid stuck transactions, get a fresh estimate right before building/signing: use query `?fresh=1` or header `X-Fee-Fresh: true` to bypass cache. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **estimateNetworkFeeRequest** | [**EstimateNetworkFeeRequest**](EstimateNetworkFeeRequest.md) |  |  |
| **fresh** | **string** | Bypass cache and fetch current fee from RPC/fee API (use right before building tx for broadcast) | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="estimatenoncustodialgas"></a>
# **EstimateNonCustodialGas**
> EstimateNonCustodialGas200Response EstimateNonCustodialGas (EstimateNonCustodialGasRequest estimateNonCustodialGasRequest)

Estimate network fee from blockchain (all supported chains; not controlled by Mudbase)

**Network fee (from blockchain only).** Returns network fee **estimated directly from the blockchain** via RPC or fee APIs. **Not controlled by Mudbase.** Both POST /api/wallet/estimate-network-fee (or calculate-fee) and this endpoint return network fee only; use either for gas/fee display. This endpoint is chain-oriented and supports full transaction shape for EVM. **EVM chains:** ethereum, polygon, arbitrum, optimism, base, bsc, binance, avalanche, celo — require `transaction` (from, and to/value or tokenAddress/amount). Response includes gasLimit, gasPrice, networkFee, estimatedTime, currency. **Non-EVM chains:** bitcoin, litecoin, dogecoin, solana, tron, ton, cardano — only `chain` is required; `transaction` is optional/ignored. Returns networkFee, estimatedTime, currency (and e.g. satPerVb for UTXO). See docs/FEE_ARCHITECTURE.md. Results cached 15s. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="generateprivatekey"></a>
# **GeneratePrivateKey**
> GeneratePrivateKey200Response GeneratePrivateKey (GeneratePrivateKeyRequest generatePrivateKeyRequest)

Generate private key


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getallfees"></a>
# **GetAllFees**
> GetAllFees200Response GetAllFees ()

Get all chain network fees (fee oracle snapshot)

Returns **all chain network fees** in one call. Reads from the fee oracle cache (no RPC during the request). Each chain returns the **full fee object** (networkFee, gasPriceGwei, congestion, estimatedTime, feeTiers for EVM, etc.) for frontend/UX. Use for dashboards or \"current fees\" screens. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getbalance"></a>
# **GetBalance**
> GetBalance200Response GetBalance (string walletId)

Get wallet balance


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getcancelparams"></a>
# **GetCancelParams**
> GetCancelParams200Response GetCancelParams (GetCancelParamsRequest getCancelParamsRequest)

Get replacement tx params for cancel (stuck EVM tx)

Returns **replacement transaction params** to cancel a stuck EVM transaction (same nonce, to=self, value=0, data=0x, higher gas). Client signs and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. EVM chains only. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getnetworkstatus"></a>
# **GetNetworkStatus**
> GetNetworkStatus200Response GetNetworkStatus ()

Get network status (congestion + fee metric per chain)

Returns **network status** per chain (congestion and main fee metric). Use to show network health before sending transactions. Same data as GET /fees but trimmed to congestion + gasPriceGwei (EVM) or satPerVb (UTXO) and networkFee. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getnoncustodialaddress"></a>
# **GetNonCustodialAddress**
> NonCustodialAddressResponse GetNonCustodialAddress (string addressId)

Get non-custodial address by ID


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getnoncustodialbalance"></a>
# **GetNonCustodialBalance**
> GetNonCustodialBalance200Response GetNonCustodialBalance (string addressId)

Get balance for a non-custodial address


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getnoncustodialtransactionbyhash"></a>
# **GetNonCustodialTransactionByHash**
> GetNonCustodialTransactionByHash200Response GetNonCustodialTransactionByHash (string txHash, string chain)

Get transaction by hash

Returns a transaction by its hash. The **chain** query parameter is required because the same hash format can exist on different chains (e.g. 0x-style on EVM chains). 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getnoncustodialtransactions"></a>
# **GetNonCustodialTransactions**
> GetNonCustodialTransactions200Response GetNonCustodialTransactions (string addressId, int limit = null, int page = null)

Get transaction history for a non-custodial address


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **limit** | **int** |  | [optional] [default to 50] |
| **page** | **int** |  | [optional] [default to 1] |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getspeedupparams"></a>
# **GetSpeedUpParams**
> GetSpeedUpParams200Response GetSpeedUpParams (GetSpeedUpParamsRequest getSpeedUpParamsRequest)

Get replacement tx params for speed-up (stuck EVM tx)

Returns **replacement transaction params** for a stuck EVM transaction (same nonce, same to/value/data, higher gas). Client signs the replacement and broadcasts via POST /api/wallet/non-custodial/broadcast. Address must be registered for your organization. Use when a tx has been pending >5 min (stuck). EVM chains only. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getsupportedcurrencies"></a>
# **GetSupportedCurrencies**
> GetSupportedCurrencies200Response GetSupportedCurrencies ()

Get supported currencies and chains

Returns the list of **platform-supported cryptocurrencies and chains** for non-custodial wallets, broadcast, and multi-chain use. Custodial wallet is no longer used in production; this endpoint is the source of truth for supported chains and currencies. **Supported:** BTC, LTC, DOGE, ETH, ETC, CELO, SOL, TRX, TON, Polygon (MATIC), Arbitrum, Optimism, Base, BSC/BNB, Avalanche (AVAX), Cardano (ADA), USDT. Each item includes **code** (currency symbol), **name** (display name), **chain** (chain id for API calls). USDT includes **networks** (ETH, BSC, TRX, SOL, POLYGON). Use **chain** with non-custodial endpoints (register-address, broadcast, estimate-gas). Use **code** for display and fee/currency selection. This is a public endpoint - no authentication required. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="gettransaction"></a>
# **GetTransaction**
> GetTransaction200Response GetTransaction (string transactionId)

Get transaction details


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="gettransactionhistory"></a>
# **GetTransactionHistory**
> GetTransactionHistory200Response GetTransactionHistory (string walletId = null, int limit = null, int page = null)

Get transaction history (custodial wallets; same monitoring as non-custodial)

Returns transaction history for custodial wallets. Transactions are stored and monitored the same way as non-custodial (WalletTransaction); status updates (pending, broadcast, confirmed, failed) and stuck detection apply to both. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **walletId** | **string** |  | [optional]  |
| **limit** | **int** |  | [optional] [default to 20] |
| **page** | **int** |  | [optional] [default to 1] |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getuserwallets"></a>
# **GetUserWallets**
> GetUserWallets200Response GetUserWallets (string projectId = null, string currency = null)

Get user wallets


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  | [optional]  |
| **currency** | **string** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getwalletfeeconfig"></a>
# **GetWalletFeeConfig**
> GetWalletFeeConfig200Response GetWalletFeeConfig (string projectId)

Get project fee configuration (for non-custodial / external users)

Get project-level fee settings (enabled flag and fee percentage). **For non-custodial / external users** — e.g. when your app charges a fee on payouts or transfers. Custodial wallet is no longer used in production. Applies to all supported chains/currencies for that project. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getwalletprivatekey"></a>
# **GetWalletPrivateKey**
> GetWalletPrivateKey200Response GetWalletPrivateKey (string walletId)

Get wallet private key (WARNING: Sensitive data; for testing non-custodial)

Returns the wallet private key. **For testing non-custodial only:** use this key to sign a transaction locally, then register the wallet address via POST /api/wallet/non-custodial/register-address and broadcast the signed tx via POST /api/wallet/non-custodial/broadcast. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getwalletwebhooklogs"></a>
# **GetWalletWebhookLogs**
> GetWalletWebhookLogs200Response GetWalletWebhookLogs (string webhookId, int limit = null)

Get webhook delivery logs


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **webhookId** | **string** |  |  |
| **limit** | **int** |  | [optional] [default to 50] |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listnoncustodialaddresses"></a>
# **ListNonCustodialAddresses**
> ListNonCustodialAddresses200Response ListNonCustodialAddresses (string chain = null, string projectId = null)

List registered non-custodial addresses


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **chain** | **string** | Filter by chain (optional) | [optional]  |
| **projectId** | **string** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listwalletwebhooks"></a>
# **ListWalletWebhooks**
> ListWalletWebhooks200Response ListWalletWebhooks (string projectId = null)

List wallet webhooks


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="registernoncustodialaddress"></a>
# **RegisterNonCustodialAddress**
> NonCustodialAddressResponse RegisterNonCustodialAddress (RegisterNonCustodialAddressRequest registerNonCustodialAddressRequest)

Register a non-custodial wallet address

Register a public wallet address for monitoring and indexing. All key operations (generation, signing) occur client-side only. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="testwalletwebhook"></a>
# **TestWalletWebhook**
> TestWalletWebhook200Response TestWalletWebhook (TestWalletWebhookRequest testWalletWebhookRequest)

Test a webhook delivery (sends a single test payload)


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatenoncustodialaddress"></a>
# **UpdateNonCustodialAddress**
> UpdateNonCustodialAddress200Response UpdateNonCustodialAddress (string addressId, UpdateNonCustodialAddressRequest updateNonCustodialAddressRequest = null)

Update a monitored wallet address

Update metadata for a registered non-custodial address. Only **label** and **derivationPath** can be updated; address and chain are immutable. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **addressId** | **string** |  |  |
| **updateNonCustodialAddressRequest** | [**UpdateNonCustodialAddressRequest**](UpdateNonCustodialAddressRequest.md) |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatewalletfeeconfig"></a>
# **UpdateWalletFeeConfig**
> UpdateWalletFeeConfig200Response UpdateWalletFeeConfig (string projectId, UpdateWalletFeeConfigRequest updateWalletFeeConfigRequest = null)

Update project fee configuration (for non-custodial / external users)

Update project-level fee settings. **For non-custodial / external users** — e.g. fee charged on payouts or transfers. Custodial wallet is no longer used in production. Applies to **all supported currencies** (BTC, ETH, BNB, LTC, SOL, TRX, USDT). **feePercentage** is a decimal: use `0.01` for 1%, `0.005` for 0.5%, etc. (min 0, max 1). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID |  |
| **updateWalletFeeConfigRequest** | [**UpdateWalletFeeConfigRequest**](UpdateWalletFeeConfigRequest.md) |  | [optional]  |

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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatewalletwebhook"></a>
# **UpdateWalletWebhook**
> UpdateWalletWebhook200Response UpdateWalletWebhook (string webhookId, UpdateWalletWebhookRequest updateWalletWebhookRequest)

Update a wallet webhook


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="validateaddress"></a>
# **ValidateAddress**
> ValidateAddress200Response ValidateAddress (ValidateAddressRequest validateAddressRequest)

Validate cryptocurrency address


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="withdraw"></a>
# **Withdraw**
> Withdraw200Response Withdraw (string walletId, WithdrawRequest withdrawRequest)

Prepare withdrawal (semi-transaction; broadcast via non-custodial)

**Semi-transaction:** Builds and signs the withdrawal but does **not** broadcast. Returns `signedTx`, `chain`, and `fromAddress` so the client can broadcast via POST /api/wallet/non-custodial/broadcast. The wallet address must be registered for your organization before broadcasting. Supports all platform chains/currencies (EVM, UTXO, Tron, Solana, USDT on ETH/BSC/TRX/SOL/POLYGON). Use for testing the non-custodial flow: create custodial wallet, get private key, register address, then call withdraw to get signed tx and broadcast it manually. 


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

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

