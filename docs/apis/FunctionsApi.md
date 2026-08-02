# Mudbase.SDK.Api.FunctionsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ActivateFunction**](FunctionsApi.md#activatefunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**CreateFunction**](FunctionsApi.md#createfunction) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**DeactivateFunction**](FunctionsApi.md#deactivatefunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**DeleteFunction**](FunctionsApi.md#deletefunction) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**ExecuteFunction**](FunctionsApi.md#executefunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**GetFunction**](FunctionsApi.md#getfunction) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**GetFunctionExecution**](FunctionsApi.md#getfunctionexecution) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId} | Get execution status |
| [**GetFunctionLogs**](FunctionsApi.md#getfunctionlogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**GetFunctionVersions**](FunctionsApi.md#getfunctionversions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**ListFunctions**](FunctionsApi.md#listfunctions) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**RetryFunctionExecution**](FunctionsApi.md#retryfunctionexecution) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**RollbackFunction**](FunctionsApi.md#rollbackfunction) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**SimulateFunctionTrigger**](FunctionsApi.md#simulatefunctiontrigger) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**TriggerFunctionWebhook**](FunctionsApi.md#triggerfunctionwebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**UpdateFunction**](FunctionsApi.md#updatefunction) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |

<a id="activatefunction"></a>
# **ActivateFunction**
> FunctionResponse ActivateFunction (string projectId, string functionId)

Activate function

Activate a deactivated function. Active functions can be triggered.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function activated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createfunction"></a>
# **CreateFunction**
> FunctionResponse CreateFunction (string projectId, CreateFunctionRequest createFunctionRequest)

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, wallet, cron, messaging. Sandbox globals available today: `payload`, `context`, `env`, `console`. Function code runs in an isolated worker with no ambient network or database access — it can only read its trigger payload, the `env` vars you configure, and return a JSON-serializable result; it cannot yet call back into your project's database, storage, messaging, or wallet APIs from inside the function body. If you need to read or write project data from a function, call the regular REST API (with your own API key) from your own backend in response to the function's returned result, rather than from within the function's own code. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createFunctionRequest** | [**CreateFunctionRequest**](CreateFunctionRequest.md) |  |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Function created |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deactivatefunction"></a>
# **DeactivateFunction**
> FunctionResponse DeactivateFunction (string projectId, string functionId)

Deactivate function

Deactivate a function. Deactivated functions will not be triggered.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deactivated |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletefunction"></a>
# **DeleteFunction**
> DeleteFunction200Response DeleteFunction (string projectId, string functionId)

Delete function

Delete a function permanently. This is a destructive operation.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deleted |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="executefunction"></a>
# **ExecuteFunction**
> FunctionExecutionResponse ExecuteFunction (string projectId, string functionId, ExecuteFunctionRequest executeFunctionRequest = null)

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour.  This endpoint is asynchronous: it returns 202 immediately with an `executionId`, before the function has necessarily finished running. Poll `GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}` until `status` leaves `queued`/`running` to get the real result, error, and duration. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **executeFunctionRequest** | [**ExecuteFunctionRequest**](ExecuteFunctionRequest.md) |  | [optional]  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Execution accepted (queued or run synchronously) — poll the executions endpoint for the outcome |  -  |
| **400** | Payload exceeds the function&#39;s configured max payload size |  -  |
| **429** | Rate limit exceeded (maxExecutionsPerMinute/maxExecutionsPerHour, or the data-mutation rate limiter) |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfunction"></a>
# **GetFunction**
> FunctionResponse GetFunction (string projectId, string functionId)

Get function

Get function details by ID including createdBy/updatedBy.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function details |  -  |
| **404** | Function not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfunctionexecution"></a>
# **GetFunctionExecution**
> FunctionExecutionStatusResponse GetFunctionExecution (string projectId, string functionId, string executionId)

Get execution status

Poll this after Execute function or Simulate trigger to get the real outcome — both of those endpoints return 202 immediately and do not carry the result themselves. `status` is one of `queued`, `provisioning`, `running`, `success`, `failed`, `timeout`; `result`/`error`/`durationMs`/`logs` are only populated once `status` leaves `queued`/`running`. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **executionId** | **string** |  |  |

### Return type

[**FunctionExecutionStatusResponse**](FunctionExecutionStatusResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Execution status |  -  |
| **404** | Execution not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfunctionlogs"></a>
# **GetFunctionLogs**
> FunctionLogsResponse GetFunctionLogs (string projectId, string functionId, int limit = null, int offset = null)

Get function execution logs

Get execution logs with pagination. Includes stats (totalExecutions, successful, failed, successRate, avgExecutionTime, lastRun).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **limit** | **int** |  | [optional] [default to 50] |
| **offset** | **int** |  | [optional] [default to 0] |

### Return type

[**FunctionLogsResponse**](FunctionLogsResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function logs and stats |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getfunctionversions"></a>
# **GetFunctionVersions**
> GetFunctionVersions200Response GetFunctionVersions (string projectId, string functionId)

Get function versions

List all code versions for a function. Used for rollback.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |

### Return type

[**GetFunctionVersions200Response**](GetFunctionVersions200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function versions |  -  |
| **404** | Function not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listfunctions"></a>
# **ListFunctions**
> FunctionListResponse ListFunctions (string projectId, int page = null, int limit = null, string search = null, string triggerType = null, bool isActive = null)

List functions

List serverless functions in a project with optional search and filters. Supports trigger types: http, event, document, file, webhook, wallet, cron, messaging. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |
| **search** | **string** | Search by name or description | [optional]  |
| **triggerType** | **string** | Filter by trigger type | [optional]  |
| **isActive** | **bool** | Filter by active status (true/false) | [optional]  |

### Return type

[**FunctionListResponse**](FunctionListResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions list |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="retryfunctionexecution"></a>
# **RetryFunctionExecution**
> FunctionExecutionResponse RetryFunctionExecution (string projectId, string functionId, int executionIndex)

Retry failed execution

Retry a failed execution by its index (0-based) in the logs. Cannot retry successful executions.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **executionIndex** | **int** | 0-based index of the execution in logs |  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry result |  -  |
| **400** | Cannot retry successful execution |  -  |
| **404** | Function or execution not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="rollbackfunction"></a>
# **RollbackFunction**
> FunctionResponse RollbackFunction (string projectId, string functionId, RollbackFunctionRequest rollbackFunctionRequest)

Rollback to previous version

Rollback function code to a previous version. Version number is required.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **rollbackFunctionRequest** | [**RollbackFunctionRequest**](RollbackFunctionRequest.md) |  |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function rolled back |  -  |
| **400** | Version number is required |  -  |
| **404** | Function or version not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="simulatefunctiontrigger"></a>
# **SimulateFunctionTrigger**
> FunctionExecutionResponse SimulateFunctionTrigger (string projectId, string functionId, SimulateFunctionTriggerRequest simulateFunctionTriggerRequest = null)

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, wallet, or cron payloads. Executes the function with the provided eventContext merged into the payload.  Asynchronous, same pattern as Execute function: returns 202 immediately with an `executionId`. Poll `GET /api/functions/projects/{projectId}/functions/{functionId}/executions/{executionId}` for the real result. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **simulateFunctionTriggerRequest** | [**SimulateFunctionTriggerRequest**](SimulateFunctionTriggerRequest.md) |  | [optional]  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Simulation accepted — poll the executions endpoint for the outcome |  -  |
| **404** | Function not found or inactive |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="triggerfunctionwebhook"></a>
# **TriggerFunctionWebhook**
> TriggerFunctionWebhook200Response TriggerFunctionWebhook (string projectId, string xWebhookSecret = null, Object body = null)

Trigger webhook functions

Public endpoint for external services to trigger functions with `trigger.type: webhook`. No authentication required. Optionally verify using `X-Webhook-Secret` header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 120 requests per 15 minutes per IP (per-org adjustable). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **xWebhookSecret** | **string** | Optional webhook secret for verification | [optional]  |
| **body** | **Object** |  | [optional]  |

### Return type

[**TriggerFunctionWebhook200Response**](TriggerFunctionWebhook200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json, application/x-www-form-urlencoded, text/plain
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions triggered successfully |  -  |
| **400** | Invalid project ID |  -  |
| **401** | Invalid webhook secret |  -  |
| **404** | Project not found |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="updatefunction"></a>
# **UpdateFunction**
> FunctionResponse UpdateFunction (string projectId, string functionId, UpdateFunctionRequest updateFunctionRequest = null)

Update function

Update function configuration. Code changes are versioned automatically.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **functionId** | **string** |  |  |
| **updateFunctionRequest** | [**UpdateFunctionRequest**](UpdateFunctionRequest.md) |  | [optional]  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function updated |  -  |
| **404** | Function not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

