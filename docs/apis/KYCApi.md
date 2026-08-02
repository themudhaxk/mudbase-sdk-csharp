# Mudbase.SDK.Api.KYCApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiKycEventsGet**](KYCApi.md#apikyceventsget) | **GET** /api/kyc/events | List recent compliance webhook deliveries |
| [**ApiKycSessionsPost**](KYCApi.md#apikycsessionspost) | **POST** /api/kyc/sessions | Start a platform KYC session |
| [**ApiKycStatusGet**](KYCApi.md#apikycstatusget) | **GET** /api/kyc/status | Get the organization&#39;s platform KYC status |
| [**ApiKycVerificationsIdGet**](KYCApi.md#apikycverificationsidget) | **GET** /api/kyc/verifications/{id} | Get a single KYC verification record |
| [**ApiKycWebhookConfigGet**](KYCApi.md#apikycwebhookconfigget) | **GET** /api/kyc/webhook-config | Get white-label KYC webhook config |
| [**ApiKycWebhookConfigPut**](KYCApi.md#apikycwebhookconfigput) | **PUT** /api/kyc/webhook-config | Set white-label KYC webhook config |
| [**ApiKycWebhookConfigTestPost**](KYCApi.md#apikycwebhookconfigtestpost) | **POST** /api/kyc/webhook-config/test | Send a signed test event to the configured webhook endpoint |
| [**ApiKycWorkflowsGet**](KYCApi.md#apikycworkflowsget) | **GET** /api/kyc/workflows | List available verification workflows |
| [**ApiProjectsProjectIdKybSessionsPost**](KYCApi.md#apiprojectsprojectidkybsessionspost) | **POST** /api/projects/{projectId}/kyb/sessions | Start a business verification (KYB) session for one of your business customers |

<a id="apikyceventsget"></a>
# **ApiKycEventsGet**
> void ApiKycEventsGet (int limit = null)

List recent compliance webhook deliveries

Audit trail of compliance webhook events received for this organization and whether Mudbase forwarded each one to the organization's own endpoint. Owner, admin, and developer roles.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **limit** | **int** | Maximum number of events to return. | [optional] [default to 25] |

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
| **200** | Recent events, newest first |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycsessionspost"></a>
# **ApiKycSessionsPost**
> void ApiKycSessionsPost (ApiKycSessionsPostRequest apiKycSessionsPostRequest = null)

Start a platform KYC session

Creates a verification session for the caller's organization. Owner/admin only.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **apiKycSessionsPostRequest** | [**ApiKycSessionsPostRequest**](ApiKycSessionsPostRequest.md) |  | [optional]  |

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
| **200** | Session created (returns the verification session URL and identifiers) |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role (owner/admin required) |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycstatusget"></a>
# **ApiKycStatusGet**
> void ApiKycStatusGet ()

Get the organization's platform KYC status


### Parameters
This endpoint does not need any parameter.
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
| **200** | Current KYC status for the caller&#39;s organization |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycverificationsidget"></a>
# **ApiKycVerificationsIdGet**
> void ApiKycVerificationsIdGet (string id)

Get a single KYC verification record


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **id** | **string** | Verification record id. |  |

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
| **200** | The verification record |  -  |
| **401** | Authentication required |  -  |
| **404** | Verification not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycwebhookconfigget"></a>
# **ApiKycWebhookConfigGet**
> ApiKycWebhookConfigGet200Response ApiKycWebhookConfigGet ()

Get white-label KYC webhook config

Returns the destination URL where the organization's own system receives KYC results and whether a signing secret is set. The secret value itself is never returned. Owner/admin only.


### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiKycWebhookConfigGet200Response**](ApiKycWebhookConfigGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Current webhook config |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role (owner/admin required) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycwebhookconfigput"></a>
# **ApiKycWebhookConfigPut**
> ApiKycWebhookConfigPut200Response ApiKycWebhookConfigPut (ApiKycWebhookConfigPutRequest apiKycWebhookConfigPutRequest = null)

Set white-label KYC webhook config

Updates the destination URL and/or signing secret used to deliver KYC results to the organization's own system. The outbound URL is SSRF-validated. When generateSecret is true a new secret is created and returned once. Owner/admin only.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **apiKycWebhookConfigPutRequest** | [**ApiKycWebhookConfigPutRequest**](ApiKycWebhookConfigPutRequest.md) |  | [optional]  |

### Return type

[**ApiKycWebhookConfigPut200Response**](ApiKycWebhookConfigPut200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated webhook config (includes webhookSecret only when freshly generated) |  -  |
| **400** | Invalid webhookUrl or webhookSecret |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role (owner/admin required) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycwebhookconfigtestpost"></a>
# **ApiKycWebhookConfigTestPost**
> ApiKycWebhookConfigTestPost200Response ApiKycWebhookConfigTestPost ()

Send a signed test event to the configured webhook endpoint

Delivers a sample `kyc.test` payload, signed exactly like a real event, so you can confirm your receiver and signature verification work. Ignores your event subscription. Owner/admin only.


### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiKycWebhookConfigTestPost200Response**](ApiKycWebhookConfigTestPost200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Delivery outcome |  -  |
| **400** | No webhook URL or signing secret configured |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role (owner/admin required) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apikycworkflowsget"></a>
# **ApiKycWorkflowsGet**
> ApiKycWorkflowsGet200Response ApiKycWorkflowsGet ()

List available verification workflows

Returns the verification workflows configured on this Mudbase account, split into kyc (individual identity) and kyb (business verification). Used to choose a default workflow in the console instead of pasting a workflow UUID. Owner/admin only.


### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiKycWorkflowsGet200Response**](ApiKycWorkflowsGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Available workflows grouped by product |  -  |
| **401** | Authentication required |  -  |
| **403** | Insufficient role (owner/admin required) |  -  |
| **503** | KYC is not configured on this server |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apiprojectsprojectidkybsessionspost"></a>
# **ApiProjectsProjectIdKybSessionsPost**
> void ApiProjectsProjectIdKybSessionsPost (string projectId, ApiProjectsProjectIdKybSessionsPostRequest apiProjectsProjectIdKybSessionsPostRequest = null)

Start a business verification (KYB) session for one of your business customers

Creates a KYB session scoped to your project. The workflow is resolved from the request, then the organization's configured default KYB workflow, then the platform default. Results arrive at your configured KYC webhook as `kyb.completed`.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **apiProjectsProjectIdKybSessionsPostRequest** | [**ApiProjectsProjectIdKybSessionsPostRequest**](ApiProjectsProjectIdKybSessionsPostRequest.md) |  | [optional]  |

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
| **201** | KYB session created (returns the hosted verification URL) |  -  |
| **400** | No KYB workflow configured, or invalid input |  -  |
| **401** | Authentication required |  -  |
| **503** | KYC is not configured on this server |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

