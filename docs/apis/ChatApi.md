# Mudbase.SDK.Api.ChatApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ChatAddParticipant**](ChatApi.md#chataddparticipant) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/participants | Add participant to chat |
| [**ChatAddReaction**](ChatApi.md#chataddreaction) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Add reaction to message |
| [**ChatCreate**](ChatApi.md#chatcreate) | **POST** /api/chat/projects/{projectId}/chats | Create new chat |
| [**ChatDeleteMessage**](ChatApi.md#chatdeletemessage) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Delete message |
| [**ChatEditMessage**](ChatApi.md#chateditmessage) | **PATCH** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Edit message |
| [**ChatGet**](ChatApi.md#chatget) | **GET** /api/chat/projects/{projectId}/chats/{chatId} | Get chat details |
| [**ChatGetMessages**](ChatApi.md#chatgetmessages) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/messages | Get chat messages |
| [**ChatList**](ChatApi.md#chatlist) | **GET** /api/chat/projects/{projectId}/chats | Get user chats |
| [**ChatMarkAsRead**](ChatApi.md#chatmarkasread) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/read | Mark messages as read |
| [**ChatRemoveParticipant**](ChatApi.md#chatremoveparticipant) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/participants | Remove participant from chat |
| [**ChatRemoveReaction**](ChatApi.md#chatremovereaction) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Remove reaction from message |
| [**ChatSendMessage**](ChatApi.md#chatsendmessage) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages | Send message |

<a id="chataddparticipant"></a>
# **ChatAddParticipant**
> ChatAddParticipant200Response ChatAddParticipant (string projectId, string chatId, ChatAddParticipantRequest chatAddParticipantRequest)

Add participant to chat

Add a user to the chat with an optional role (admin or member).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **chatAddParticipantRequest** | [**ChatAddParticipantRequest**](ChatAddParticipantRequest.md) | User ID to add and optional role (admin, member). |  |

### Return type

[**ChatAddParticipant200Response**](ChatAddParticipant200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant added |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chataddreaction"></a>
# **ChatAddReaction**
> ChatAddReaction200Response ChatAddReaction (string projectId, string chatId, string messageId, ChatAddReactionRequest chatAddReactionRequest)

Add reaction to message

Add an emoji reaction to a message.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **messageId** | **string** | Message ID. |  |
| **chatAddReactionRequest** | [**ChatAddReactionRequest**](ChatAddReactionRequest.md) | Emoji reaction (e.g. 👍, ❤️). |  |

### Return type

[**ChatAddReaction200Response**](ChatAddReaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction added |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatcreate"></a>
# **ChatCreate**
> ChatCreate201Response ChatCreate (string projectId, ChatCreateRequest chatCreateRequest)

Create new chat

Create a new chat (direct, group, channel, or broadcast) with name, type, participants, and optional settings.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatCreateRequest** | [**ChatCreateRequest**](ChatCreateRequest.md) | Chat name, type (direct/group/channel/broadcast), participants array, optional description and settings. |  |

### Return type

[**ChatCreate201Response**](ChatCreate201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Chat created |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatdeletemessage"></a>
# **ChatDeleteMessage**
> MessageResponse ChatDeleteMessage (string projectId, string chatId, string messageId)

Delete message

Delete a message from the chat (sender or admin). May be soft-delete or permanent depending on implementation.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **messageId** | **string** | Message ID. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message deleted |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chateditmessage"></a>
# **ChatEditMessage**
> ChatEditMessage200Response ChatEditMessage (string projectId, string chatId, string messageId, ChatEditMessageRequest chatEditMessageRequest)

Edit message

Update the content of a message (sender only; supports edit history).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **messageId** | **string** | Message ID. |  |
| **chatEditMessageRequest** | [**ChatEditMessageRequest**](ChatEditMessageRequest.md) | New message content. |  |

### Return type

[**ChatEditMessage200Response**](ChatEditMessage200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message edited |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **403** | Access denied. The **error** field contains the exact backend message, e.g. \&quot;Access denied\&quot;, \&quot;Insufficient permissions\&quot;, \&quot;You don&#39;t have permission to view this organization&#39;s projects\&quot;, \&quot;Account suspended\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatget"></a>
# **ChatGet**
> ChatGet200Response ChatGet (string projectId, string chatId)

Get chat details

Returns full chat metadata including participants and roles for a single chat.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |

### Return type

[**ChatGet200Response**](ChatGet200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Chat details |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |
| **404** | Project not found (exact backend message for project endpoints). |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatgetmessages"></a>
# **ChatGetMessages**
> ChatGetMessages200Response ChatGetMessages (string projectId, string chatId, int page = null, int limit = null, DateTime before = null, DateTime after = null)

Get chat messages

Returns paginated messages for a chat with optional before/after cursor for time-based pagination.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **page** | **int** | Page number (1-based). | [optional] [default to 1] |
| **limit** | **int** | Number of messages per page. | [optional] [default to 50] |
| **before** | **DateTime** | Return messages before this timestamp (cursor). | [optional]  |
| **after** | **DateTime** | Return messages after this timestamp (cursor). | [optional]  |

### Return type

[**ChatGetMessages200Response**](ChatGetMessages200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatlist"></a>
# **ChatList**
> ChatList200Response ChatList (string projectId, int page = null, int limit = null)

Get user chats

Returns paginated list of chats for the current user in the project, with last message and unread count.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **page** | **int** | Page number (1-based). | [optional] [default to 1] |
| **limit** | **int** | Number of chats per page. | [optional] [default to 20] |

### Return type

[**ChatList200Response**](ChatList200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User chats list |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatmarkasread"></a>
# **ChatMarkAsRead**
> ChatMarkAsRead200Response ChatMarkAsRead (string projectId, string chatId, ChatMarkAsReadRequest chatMarkAsReadRequest)

Mark messages as read

Mark one or more messages as read for the current user in the chat.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **chatMarkAsReadRequest** | [**ChatMarkAsReadRequest**](ChatMarkAsReadRequest.md) | Array of message IDs to mark as read. |  |

### Return type

[**ChatMarkAsRead200Response**](ChatMarkAsRead200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages marked as read |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatremoveparticipant"></a>
# **ChatRemoveParticipant**
> MessageResponse ChatRemoveParticipant (string projectId, string chatId, ChatRemoveParticipantRequest chatRemoveParticipantRequest)

Remove participant from chat

Remove a user from the chat by userId.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **chatRemoveParticipantRequest** | [**ChatRemoveParticipantRequest**](ChatRemoveParticipantRequest.md) | User ID of the participant to remove. |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant removed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatremovereaction"></a>
# **ChatRemoveReaction**
> ChatRemoveReaction200Response ChatRemoveReaction (string projectId, string chatId, string messageId, ChatAddReactionRequest chatAddReactionRequest)

Remove reaction from message

Remove the current user's emoji reaction from a message.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **messageId** | **string** | Message ID. |  |
| **chatAddReactionRequest** | [**ChatAddReactionRequest**](ChatAddReactionRequest.md) | Emoji to remove (must match the reaction added by the user). |  |

### Return type

[**ChatRemoveReaction200Response**](ChatRemoveReaction200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction removed |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="chatsendmessage"></a>
# **ChatSendMessage**
> ChatSendMessage201Response ChatSendMessage (string projectId, string chatId, ChatSendMessageRequest chatSendMessageRequest)

Send message

Send a message (text, image, video, audio, file, location, contact) to a chat with optional replyTo and mentions.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** | Project ID. |  |
| **chatId** | **string** | Chat ID. |  |
| **chatSendMessageRequest** | [**ChatSendMessageRequest**](ChatSendMessageRequest.md) | Message type, content, optional replyTo and mentions. |  |

### Return type

[**ChatSendMessage201Response**](ChatSendMessage201Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Message sent |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

