# Mudbase.SDK.Api.MessagingApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**MessagingGetHistory**](MessagingApi.md#messaginggethistory) | **GET** /api/messaging/projects/{projectId}/messaging/history | Get message history |
| [**MessagingGetStats**](MessagingApi.md#messaginggetstats) | **GET** /api/messaging/projects/{projectId}/messaging/stats | Get message statistics |
| [**MessagingSendEmail**](MessagingApi.md#messagingsendemail) | **POST** /api/messaging/projects/{projectId}/messaging/email | Send transactional email |
| [**MessagingSendPush**](MessagingApi.md#messagingsendpush) | **POST** /api/messaging/projects/{projectId}/messaging/push | Send push notification |
| [**MessagingSendSms**](MessagingApi.md#messagingsendsms) | **POST** /api/messaging/projects/{projectId}/messaging/sms | Send SMS to one or more recipients (E.164 format) |

<a id="messaginggethistory"></a>
# **MessagingGetHistory**
> MessageHistoryResponse MessagingGetHistory (string projectId, string type = null, int page = null, int limit = null, string status = null)

Get message history

Get message history (push, email, SMS) with filtering and pagination. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the messaging project. |  |
| **type** | **string** | Filter by message type (push, email, or sms). | [optional]  |
| **page** | **int** | Page number for pagination (1-based). | [optional] [default to 1] |
| **limit** | **int** | Maximum number of messages per page. | [optional] [default to 20] |
| **status** | **string** | Filter by delivery status. | [optional]  |

### Return type

[**MessageHistoryResponse**](MessageHistoryResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message history |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="messaginggetstats"></a>
# **MessagingGetStats**
> MessageStatsResponse MessagingGetStats (string projectId, DateTime startDate = null, DateTime endDate = null)

Get message statistics

Get messaging statistics including total messages, success rates, and breakdown by type (push, email, SMS). Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the messaging project. |  |
| **startDate** | **DateTime** | Start of the date range for statistics (ISO 8601). | [optional]  |
| **endDate** | **DateTime** | End of the date range for statistics (ISO 8601). | [optional]  |

### Return type

[**MessageStatsResponse**](MessageStatsResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message statistics |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="messagingsendemail"></a>
# **MessagingSendEmail**
> MessageSentResponse MessagingSendEmail (string projectId, EmailRequest emailRequest)

Send transactional email

Send a transactional email to one or more recipients. Supports HTML and plain text. Use for verification emails, password resets, notifications, and marketing. Attachments and templates can be configured per project. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the messaging project. |  |
| **emailRequest** | [**EmailRequest**](EmailRequest.md) | Recipient(s), subject, HTML and/or plain text body; optional reply-to and attachments. |  |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Email sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="messagingsendpush"></a>
# **MessagingSendPush**
> MessageSentResponse MessagingSendPush (string projectId, PushNotificationRequest pushNotificationRequest)

Send push notification

Send a push notification to one or more devices. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the messaging project. |  |
| **pushNotificationRequest** | [**PushNotificationRequest**](PushNotificationRequest.md) | Device tokens, notification title/body, optional data payload and image URL. |  |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Push notification sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="messagingsendsms"></a>
# **MessagingSendSms**
> MessageSentResponse MessagingSendSms (string projectId, SMSRequest sMSRequest)

Send SMS to one or more recipients (E.164 format)

Send an SMS message to one or more phone numbers in E.164 format. Accepts BearerToken (JWT) or ApiKeyAuth (X-API-Key). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID (MongoDB ObjectId) for the messaging project. |  |
| **sMSRequest** | [**SMSRequest**](SMSRequest.md) | Recipient phone number(s), message body, and optional sender ID. |  |

### Return type

[**MessageSentResponse**](MessageSentResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | SMS sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

