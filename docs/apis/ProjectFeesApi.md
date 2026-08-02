# Mudbase.SDK.Api.ProjectFeesApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ConfirmAddressVerification**](ProjectFeesApi.md#confirmaddressverification) | **POST** /api/projects/{projectId}/fee-settings/{currency}/confirm-verification | ~~Confirm address verification~~ (deprecated) |
| [**CreateOrUpdateFeeSettings**](ProjectFeesApi.md#createorupdatefeesettings) | **POST** /api/projects/{projectId}/fee-settings | ~~Create or update project fee settings~~ (deprecated) |
| [**GetCurrencyFeeBalance**](ProjectFeesApi.md#getcurrencyfeebalance) | **GET** /api/projects/{projectId}/fee-balances/{currency} | ~~Get currency fee balance~~ (deprecated) |
| [**GetFeeBalances**](ProjectFeesApi.md#getfeebalances) | **GET** /api/projects/{projectId}/fee-balances | ~~Get all fee balances~~ (deprecated) |
| [**GetFeeSettings**](ProjectFeesApi.md#getfeesettings) | **GET** /api/projects/{projectId}/fee-settings | ~~Get project fee settings~~ (deprecated) |
| [**GetPayoutHistory**](ProjectFeesApi.md#getpayouthistory) | **GET** /api/projects/{projectId}/payout-history | ~~Get payout history~~ (deprecated) |
| [**GetProjectFeeDashboard**](ProjectFeesApi.md#getprojectfeedashboard) | **GET** /api/projects/{projectId}/fee-dashboard | ~~Get fee dashboard~~ (deprecated) |
| [**InitiateAddressVerification**](ProjectFeesApi.md#initiateaddressverification) | **POST** /api/projects/{projectId}/fee-settings/{currency}/verify-address | ~~Initiate address verification~~ (deprecated) |
| [**RequestManualPayout**](ProjectFeesApi.md#requestmanualpayout) | **POST** /api/projects/{projectId}/payouts/request-manual | ~~Request manual payout~~ (deprecated) |
| [**UpdateCurrencyFeeSettings**](ProjectFeesApi.md#updatecurrencyfeesettings) | **PATCH** /api/projects/{projectId}/fee-settings/{currency} | ~~Update currency fee settings~~ (deprecated) |

<a id="confirmaddressverification"></a>
# **ConfirmAddressVerification**
> ConfirmAddressVerification200Response ConfirmAddressVerification (string projectId, string currency, ConfirmAddressVerificationRequest confirmAddressVerificationRequest)

~~Confirm address verification~~ (deprecated)

Confirm address verification by providing the transaction hash of the test transaction sent to the payout address. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **currency** | **string** |  |  |
| **confirmAddressVerificationRequest** | [**ConfirmAddressVerificationRequest**](ConfirmAddressVerificationRequest.md) |  |  |

### Return type

[**ConfirmAddressVerification200Response**](ConfirmAddressVerification200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Address verified |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createorupdatefeesettings"></a>
# **CreateOrUpdateFeeSettings**
> ApplyRoleFeaturePreset200Response CreateOrUpdateFeeSettings (string projectId, CreateOrUpdateFeeSettingsRequest createOrUpdateFeeSettingsRequest)

~~Create or update project fee settings~~ (deprecated)

Create or update fee settings for a project. Configure transaction fees, payout addresses, and thresholds for supported cryptocurrencies. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createOrUpdateFeeSettingsRequest** | [**CreateOrUpdateFeeSettingsRequest**](CreateOrUpdateFeeSettingsRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee settings updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getcurrencyfeebalance"></a>
# **GetCurrencyFeeBalance**
> GetCurrencyFeeBalance200Response GetCurrencyFeeBalance (string projectId, string currency)

~~Get currency fee balance~~ (deprecated)

Get fee balance for a specific cryptocurrency in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **currency** | **string** |  |  |

### Return type

[**GetCurrencyFeeBalance200Response**](GetCurrencyFeeBalance200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Currency balance |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfeebalances"></a>
# **GetFeeBalances**
> GetFeeBalances200Response GetFeeBalances (string projectId)

~~Get all fee balances~~ (deprecated)

Get fee balances for all currencies in a project, including collected amounts, thresholds, and payout status. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetFeeBalances200Response**](GetFeeBalances200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee balances |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfeesettings"></a>
# **GetFeeSettings**
> TestWalletWebhook200Response GetFeeSettings (string projectId)

~~Get project fee settings~~ (deprecated)

Get all fee settings configured for a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**TestWalletWebhook200Response**](TestWalletWebhook200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee settings |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getpayouthistory"></a>
# **GetPayoutHistory**
> GetPayoutHistory200Response GetPayoutHistory (string projectId, int limit = null, int page = null, string currency = null, string status = null)

~~Get payout history~~ (deprecated)

Get historical payout records for a project with pagination. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **limit** | **int** |  | [optional] [default to 20] |
| **page** | **int** |  | [optional] [default to 1] |
| **currency** | **string** |  | [optional]  |
| **status** | **string** |  | [optional]  |

### Return type

[**GetPayoutHistory200Response**](GetPayoutHistory200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payout history |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectfeedashboard"></a>
# **GetProjectFeeDashboard**
> GetProjectFeeDashboard200Response GetProjectFeeDashboard (string projectId)

~~Get fee dashboard~~ (deprecated)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetProjectFeeDashboard200Response**](GetProjectFeeDashboard200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Fee dashboard data |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="initiateaddressverification"></a>
# **InitiateAddressVerification**
> InitiateAddressVerification200Response InitiateAddressVerification (string projectId, string currency)

~~Initiate address verification~~ (deprecated)

Initiate verification process for a payout address. Requires sending a small test transaction to verify ownership. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **currency** | **string** |  |  |

### Return type

[**InitiateAddressVerification200Response**](InitiateAddressVerification200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Verification initiated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="requestmanualpayout"></a>
# **RequestManualPayout**
> ApplyRoleFeaturePreset200Response RequestManualPayout (string projectId, RequestManualPayoutRequest requestManualPayoutRequest)

~~Request manual payout~~ (deprecated)

Request a manual payout for collected fees. Requires sufficient balance above the threshold. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **requestManualPayoutRequest** | [**RequestManualPayoutRequest**](RequestManualPayoutRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Manual payout requested |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatecurrencyfeesettings"></a>
# **UpdateCurrencyFeeSettings**
> ApplyRoleFeaturePreset200Response UpdateCurrencyFeeSettings (string projectId, string currency, UpdateCurrencyFeeSettingsRequest updateCurrencyFeeSettingsRequest)

~~Update currency fee settings~~ (deprecated)

Update fee settings for a specific cryptocurrency in a project. Accepts: OrgBearerAuth (for admin users), ProjectBearerAuth (JWT for authenticated users), or ApiKeyAuth (X-API-Key for programmatic access). Both ProjectBearerAuth and ApiKeyAuth are fully implemented. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **currency** | **string** |  |  |
| **updateCurrencyFeeSettingsRequest** | [**UpdateCurrencyFeeSettingsRequest**](UpdateCurrencyFeeSettingsRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Currency fee settings updated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

