# Mudbase.SDK.Api.FunctionsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**FunctionsActivate**](FunctionsApi.md#functionsactivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/activate | Activate function |
| [**FunctionsCreate**](FunctionsApi.md#functionscreate) | **POST** /api/functions/projects/{projectId}/functions | Create function |
| [**FunctionsDeactivate**](FunctionsApi.md#functionsdeactivate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/deactivate | Deactivate function |
| [**FunctionsDelete**](FunctionsApi.md#functionsdelete) | **DELETE** /api/functions/projects/{projectId}/functions/{functionId} | Delete function |
| [**FunctionsExecute**](FunctionsApi.md#functionsexecute) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/execute | Execute function |
| [**FunctionsGet**](FunctionsApi.md#functionsget) | **GET** /api/functions/projects/{projectId}/functions/{functionId} | Get function |
| [**FunctionsGetLogs**](FunctionsApi.md#functionsgetlogs) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/logs | Get function execution logs |
| [**FunctionsGetVersions**](FunctionsApi.md#functionsgetversions) | **GET** /api/functions/projects/{projectId}/functions/{functionId}/versions | Get function versions |
| [**FunctionsList**](FunctionsApi.md#functionslist) | **GET** /api/functions/projects/{projectId}/functions | List functions |
| [**FunctionsRetry**](FunctionsApi.md#functionsretry) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/retry/{executionIndex} | Retry failed execution |
| [**FunctionsRollback**](FunctionsApi.md#functionsrollback) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/rollback | Rollback to previous version |
| [**FunctionsSimulate**](FunctionsApi.md#functionssimulate) | **POST** /api/functions/projects/{projectId}/functions/{functionId}/simulate | Simulate trigger |
| [**FunctionsTriggerWebhook**](FunctionsApi.md#functionstriggerwebhook) | **POST** /api/functions/webhook/{projectId} | Trigger webhook functions |
| [**FunctionsUpdate**](FunctionsApi.md#functionsupdate) | **PUT** /api/functions/projects/{projectId}/functions/{functionId} | Update function |

<a id="functionsactivate"></a>
# **FunctionsActivate**
> FunctionResponse FunctionsActivate (string projectId, string functionId)

Activate function

Activate a deactivated function. Active functions can be triggered.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to activate. |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function activated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionscreate"></a>
# **FunctionsCreate**
> FunctionResponse FunctionsCreate (string projectId, CreateFunctionRequest createFunctionRequest)

Create function

Create a new serverless function. Trigger types: http, document, file, webhook, wallet, cron, messaging. Sandbox utilities available: db, files, messaging, wallet, utils, env, console. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **createFunctionRequest** | [**CreateFunctionRequest**](CreateFunctionRequest.md) | Function name, description, code, trigger config, and optional environment. |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Function created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsdeactivate"></a>
# **FunctionsDeactivate**
> FunctionResponse FunctionsDeactivate (string projectId, string functionId)

Deactivate function

Deactivate a function. Deactivated functions will not be triggered.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to deactivate. |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deactivated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsdelete"></a>
# **FunctionsDelete**
> FunctionsDelete200Response FunctionsDelete (string projectId, string functionId)

Delete function

Delete a function permanently. This is a destructive operation.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **functionId** | **string** | Function ID to delete. |  |

### Return type

[**FunctionsDelete200Response**](FunctionsDelete200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsexecute"></a>
# **FunctionsExecute**
> FunctionExecutionResponse FunctionsExecute (string projectId, string functionId, FunctionsExecuteRequest functionsExecuteRequest = null)

Execute function

Manually execute a function with custom payload. Payload is merged with auto-injected trigger context. Rate limited (data mutation rate limiter). Enforces maxExecutionsPerMinute/maxExecutionsPerHour. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to execute. |  |
| **functionsExecuteRequest** | [**FunctionsExecuteRequest**](FunctionsExecuteRequest.md) | Optional JSON payload merged with trigger context (e.g. document, file, webhook body). Omit for no custom input. | [optional]  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function executed successfully |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsget"></a>
# **FunctionsGet**
> FunctionResponse FunctionsGet (string projectId, string functionId)

Get function

Get function details by ID including createdBy/updatedBy.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **functionId** | **string** | Function ID. |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsgetlogs"></a>
# **FunctionsGetLogs**
> FunctionLogsResponse FunctionsGetLogs (string projectId, string functionId, int limit = null, int offset = null)

Get function execution logs

Get execution logs with pagination. Includes stats (totalExecutions, successful, failed, successRate, avgExecutionTime, lastRun).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to get logs for. |  |
| **limit** | **int** | Maximum number of log entries to return. | [optional] [default to 50] |
| **offset** | **int** | Number of log entries to skip for pagination. | [optional] [default to 0] |

### Return type

[**FunctionLogsResponse**](FunctionLogsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function logs and stats |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsgetversions"></a>
# **FunctionsGetVersions**
> FunctionsGetVersions200Response FunctionsGetVersions (string projectId, string functionId)

Get function versions

List all code versions for a function. Used for rollback.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to list versions for. |  |

### Return type

[**FunctionsGetVersions200Response**](FunctionsGetVersions200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function versions |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionslist"></a>
# **FunctionsList**
> FunctionListResponse FunctionsList (string projectId, int page = null, int limit = null, string search = null, string triggerType = null, bool isActive = null)

List functions

List serverless functions in a project with optional search and filters. Supports trigger types: http, event, document, file, webhook, wallet, cron, messaging. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **page** | **int** | Page number (1-based). | [optional] [default to 1] |
| **limit** | **int** | Number of functions per page. | [optional] [default to 20] |
| **search** | **string** | Search by name or description | [optional]  |
| **triggerType** | **string** | Filter by trigger type | [optional]  |
| **isActive** | **bool** | Filter by active status (true/false) | [optional]  |

### Return type

[**FunctionListResponse**](FunctionListResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Functions list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsretry"></a>
# **FunctionsRetry**
> FunctionExecutionResponse FunctionsRetry (string projectId, string functionId, int executionIndex)

Retry failed execution

Retry a failed execution by its index (0-based) in the logs. Cannot retry successful executions.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to retry execution for. |  |
| **executionIndex** | **int** | 0-based index of the execution in logs |  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Retry result |  -  |
| **400** | Cannot retry successful execution |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsrollback"></a>
# **FunctionsRollback**
> FunctionResponse FunctionsRollback (string projectId, string functionId, FunctionsRollbackRequest functionsRollbackRequest)

Rollback to previous version

Rollback function code to a previous version. Version number is required.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to rollback. |  |
| **functionsRollbackRequest** | [**FunctionsRollbackRequest**](FunctionsRollbackRequest.md) | Version number (integer) to rollback to; use GET .../versions to list available versions. |  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function rolled back |  -  |
| **400** | Version number is required |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionssimulate"></a>
# **FunctionsSimulate**
> FunctionExecutionResponse FunctionsSimulate (string projectId, string functionId, FunctionsSimulateRequest functionsSimulateRequest = null)

Simulate trigger

Test a function with simulated trigger context. Use to verify document, file, webhook, wallet, or cron payloads. Executes the function with the provided eventContext merged into the payload. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) that owns the function. |  |
| **functionId** | **string** | Function ID (MongoDB ObjectId) to simulate. |  |
| **functionsSimulateRequest** | [**FunctionsSimulateRequest**](FunctionsSimulateRequest.md) | Simulated trigger (type, event) and eventContext (document, file, webhook, wallet, message, or cron). Merged into the function payload for testing. | [optional]  |

### Return type

[**FunctionExecutionResponse**](FunctionExecutionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Simulation result |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionstriggerwebhook"></a>
# **FunctionsTriggerWebhook**
> FunctionsTriggerWebhook200Response FunctionsTriggerWebhook (string projectId, string xWebhookSecret = null, Object body = null)

Trigger webhook functions

Public endpoint for external services to trigger functions with `trigger.type: webhook`. No authentication required. Optionally verify using `X-Webhook-Secret` header (configure per project or via FUNCTION_WEBHOOK_SECRET). Rate limited to 30 requests per 15 minutes per IP. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **xWebhookSecret** | **string** | Optional webhook secret for verification | [optional]  |
| **body** | **Object** | Payload sent to the triggered function(s). | [optional]  |

### Return type

[**FunctionsTriggerWebhook200Response**](FunctionsTriggerWebhook200Response.md)

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
| **404** | Project not found (exact backend message for project endpoints). |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="functionsupdate"></a>
# **FunctionsUpdate**
> FunctionResponse FunctionsUpdate (string projectId, string functionId, UpdateFunctionRequest updateFunctionRequest = null)

Update function

Update function configuration. Code changes are versioned automatically.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **functionId** | **string** | Function ID. |  |
| **updateFunctionRequest** | [**UpdateFunctionRequest**](UpdateFunctionRequest.md) | Fields to update (name, description, code, trigger, environment, isActive, limits, retryPolicy). | [optional]  |

### Return type

[**FunctionResponse**](FunctionResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Function updated |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Function not found (exact backend message for functions endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

