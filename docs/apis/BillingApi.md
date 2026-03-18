# Mudbase.SDK.Api.BillingApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**BillingCheckFeatureAccess**](BillingApi.md#billingcheckfeatureaccess) | **GET** /api/billing/public/projects/{projectId}/feature-access | Check feature access (public) |
| [**BillingCheckSubscription**](BillingApi.md#billingchecksubscription) | **GET** /api/billing/public/projects/{projectId}/subscription | Check subscription status (public) |
| [**BillingCreateCheckoutSession**](BillingApi.md#billingcreatecheckoutsession) | **POST** /api/billing/public/projects/{projectId}/checkout | Create checkout session (Flutterwave or crypto) |
| [**BillingGetCheckoutPayment**](BillingApi.md#billinggetcheckoutpayment) | **GET** /api/billing/public/projects/{projectId}/checkout/{paymentId} | Get checkout payment details |
| [**BillingGetPublicPlans**](BillingApi.md#billinggetpublicplans) | **GET** /api/billing/public/projects/{projectId}/plans | Get public plans (no auth required) |
| [**BillingHandleCryptoWebhook**](BillingApi.md#billinghandlecryptowebhook) | **POST** /api/billing/webhooks/crypto | Crypto payment processor webhook |
| [**BillingHandleFlutterwaveWebhook**](BillingApi.md#billinghandleflutterwavewebhook) | **POST** /api/billing/webhooks/flutterwave | Flutterwave webhook |
| [**BillingInitializePayment**](BillingApi.md#billinginitializepayment) | **POST** /api/projects/{projectId}/payment-processing/initialize-payment | Initialize fiat payment (app-scoped) |
| [**BillingRecordUsage**](BillingApi.md#billingrecordusage) | **POST** /api/billing/public/projects/{projectId}/usage | Record usage (public) |
| [**BillingVerifyPayment**](BillingApi.md#billingverifypayment) | **POST** /api/billing/public/projects/{projectId}/verify-payment | Verify payment and create subscription |

<a id="billingcheckfeatureaccess"></a>
# **BillingCheckFeatureAccess**
> BillingCheckFeatureAccess200Response BillingCheckFeatureAccess (string projectId, string email, string feature)

Check feature access (public)

Check whether a customer has access to a feature (by plan or entitlement). Public; no auth required.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **email** | **string** | Customer email |  |
| **feature** | **string** | Feature slug to check access for |  |

### Return type

[**BillingCheckFeatureAccess200Response**](BillingCheckFeatureAccess200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Feature access status |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billingchecksubscription"></a>
# **BillingCheckSubscription**
> BillingCheckSubscription200Response BillingCheckSubscription (string projectId, string email)

Check subscription status (public)

Check whether a customer (by email) has an active subscription for the project. Public; no auth required.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **email** | **string** | Customer email to check subscription for |  |

### Return type

[**BillingCheckSubscription200Response**](BillingCheckSubscription200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Subscription status |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billingcreatecheckoutsession"></a>
# **BillingCreateCheckoutSession**
> BillingCreateCheckoutSession200Response BillingCreateCheckoutSession (string projectId, BillingCreateCheckoutSessionRequest billingCreateCheckoutSessionRequest)

Create checkout session (Flutterwave or crypto)

Creates a checkout session for subscription billing. When Flutterwave is configured (platform), returns authorizationUrl and accessCode for redirect. When using crypto payment processor, returns checkoutUrl, paymentOptions (multi-chain USDC/USDT/BTC Lightning), and reference. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **billingCreateCheckoutSessionRequest** | [**BillingCreateCheckoutSessionRequest**](BillingCreateCheckoutSessionRequest.md) | Plan to subscribe to, billing cycle, customer email/name, and optional success/cancel redirect URLs. |  |

### Return type

[**BillingCreateCheckoutSession200Response**](BillingCreateCheckoutSession200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Checkout session created |  -  |
| **400** | Missing planId, billingCycle, or customerInfo.email |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billinggetcheckoutpayment"></a>
# **BillingGetCheckoutPayment**
> BillingGetCheckoutPayment200Response BillingGetCheckoutPayment (string projectId, string paymentId)

Get checkout payment details

Returns payment intent/checkout status (for refresh or deep link). No auth required.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **paymentId** | **string** | Payment ID or reference from checkout session |  |

### Return type

[**BillingGetCheckoutPayment200Response**](BillingGetCheckoutPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Payment not found (exact backend message for payment admin endpoints). |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billinggetpublicplans"></a>
# **BillingGetPublicPlans**
> BillingGetPublicPlans200Response BillingGetPublicPlans (string projectId)

Get public plans (no auth required)

Returns subscription plans available for the project. Public; no authentication required. Use for pricing pages and checkout flow.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) to list plans for. |  |

### Return type

[**BillingGetPublicPlans200Response**](BillingGetPublicPlans200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Public plans list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billinghandlecryptowebhook"></a>
# **BillingHandleCryptoWebhook**
> BillingHandleCryptoWebhook200Response BillingHandleCryptoWebhook (BillingHandleCryptoWebhookRequest billingHandleCryptoWebhookRequest)

Crypto payment processor webhook

Receives crypto payment events (payment.completed, etc.) for platform billing. No auth; verified by provider signature.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **billingHandleCryptoWebhookRequest** | [**BillingHandleCryptoWebhookRequest**](BillingHandleCryptoWebhookRequest.md) | Crypto payment webhook payload (event type and data with paymentId, reference, amount, currency, network, status, metadata). |  |

### Return type

[**BillingHandleCryptoWebhook200Response**](BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook processed |  -  |
| **400** | Event type is required or invalid payload |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billinghandleflutterwavewebhook"></a>
# **BillingHandleFlutterwaveWebhook**
> BillingHandleCryptoWebhook200Response BillingHandleFlutterwaveWebhook (BillingHandleFlutterwaveWebhookRequest billingHandleFlutterwaveWebhookRequest)

Flutterwave webhook

Receives Flutterwave webhook events (charge.completed, payment.successful). No auth; verified by verif-hash header. - Subscription billing: meta without isPaymentProcessing triggers verifyPaymentAndCreateSubscription (mudbase_xxx refs). - Payment processing: meta.isPaymentProcessing === true triggers fiat payment record (mudbase_fiat_xxx refs); org share goes to org subaccount, platform fee to main or configured subaccounts. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **billingHandleFlutterwaveWebhookRequest** | [**BillingHandleFlutterwaveWebhookRequest**](BillingHandleFlutterwaveWebhookRequest.md) | Flutterwave webhook payload (event and data with id, tx_ref, amount, currency, status, customer, meta for subscription or payment-processing). |  |

### Return type

[**BillingHandleCryptoWebhook200Response**](BillingHandleCryptoWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Webhook received |  -  |
| **400** | Invalid or missing event |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billinginitializepayment"></a>
# **BillingInitializePayment**
> void BillingInitializePayment (string projectId, BillingInitializePaymentRequest billingInitializePaymentRequest)

Initialize fiat payment (app-scoped)

Same as org-level initialize-payment; projectId from path is used for scope and tx_ref. Resolves project to org and uses org's Flutterwave subaccount.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID for payment scope and tx_ref. |  |
| **billingInitializePaymentRequest** | [**BillingInitializePaymentRequest**](BillingInitializePaymentRequest.md) | Payment amount, currency, customer (email, name), and optional metadata. |  |

### Return type

void (empty response body)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment link and fee breakdown (same shape as org-level) |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billingrecordusage"></a>
# **BillingRecordUsage**
> MessageResponse BillingRecordUsage (string projectId, BillingRecordUsageRequest billingRecordUsageRequest)

Record usage (public)

Record metered usage for a customer (e.g. api_calls, storage_mb). Used for usage-based billing. Public endpoint; optionally secured by webhook or API key in production.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **billingRecordUsageRequest** | [**BillingRecordUsageRequest**](BillingRecordUsageRequest.md) | Customer email, metric name (e.g. api_calls, storage_mb), and quantity to record. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Usage recorded |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="billingverifypayment"></a>
# **BillingVerifyPayment**
> BillingVerifyPayment200Response BillingVerifyPayment (string projectId, string reference)

Verify payment and create subscription

Verifies payment by reference (Flutterwave mudbase_xxx or crypto pmt_xxx) and creates or updates the subscription. Call after redirect from payment provider; pass reference as query (e.g. ?reference=mudbase_abc123). Idempotent for same reference. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the billing project. |  |
| **reference** | **string** | Payment reference (e.g. mudbase_abc123 or pmt_abc123) |  |

### Return type

[**BillingVerifyPayment200Response**](BillingVerifyPayment200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Payment verified and subscription created |  -  |
| **400** | reference is required or organization context missing |  -  |
| **403** | Payment does not belong to your organization |  -  |
| **500** | Server error. The **error** field contains the exact backend message, e.g. \&quot;Authentication failed\&quot;, \&quot;Failed to upload file\&quot;, \&quot;Failed to fetch project\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

