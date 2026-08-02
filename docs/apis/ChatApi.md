# Mudbase.SDK.Api.ChatApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**AddParticipant**](ChatApi.md#addparticipant) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/participants | Add participant to chat |
| [**AddReaction**](ChatApi.md#addreaction) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Add reaction to message |
| [**CreateChat**](ChatApi.md#createchat) | **POST** /api/chat/projects/{projectId}/chats | Create new chat |
| [**DeleteMessage**](ChatApi.md#deletemessage) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Delete message |
| [**EditMessage**](ChatApi.md#editmessage) | **PATCH** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId} | Edit message |
| [**GetChatDetails**](ChatApi.md#getchatdetails) | **GET** /api/chat/projects/{projectId}/chats/{chatId} | Get chat details |
| [**GetChatE2eeParticipantKeys**](ChatApi.md#getchate2eeparticipantkeys) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/e2ee/participant-keys | List participant E2EE public keys |
| [**GetChatMessages**](ChatApi.md#getchatmessages) | **GET** /api/chat/projects/{projectId}/chats/{chatId}/messages | Get chat messages |
| [**GetUserChats**](ChatApi.md#getuserchats) | **GET** /api/chat/projects/{projectId}/chats | Get user chats |
| [**MarkMessagesAsRead**](ChatApi.md#markmessagesasread) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages/read | Mark messages as read |
| [**PutChatE2eeKey**](ChatApi.md#putchate2eekey) | **PUT** /api/chat/projects/{projectId}/me/chat-e2ee-key | Register chat E2EE identity public key |
| [**RemoveParticipant**](ChatApi.md#removeparticipant) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/participants | Remove participant from chat |
| [**RemoveReaction**](ChatApi.md#removereaction) | **DELETE** /api/chat/projects/{projectId}/chats/{chatId}/messages/{messageId}/reactions | Remove reaction from message |
| [**SendMessage**](ChatApi.md#sendmessage) | **POST** /api/chat/projects/{projectId}/chats/{chatId}/messages | Send message |

<a id="addparticipant"></a>
# **AddParticipant**
> AddParticipant200Response AddParticipant (string projectId, string chatId, AddParticipantRequest addParticipantRequest)

Add participant to chat


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **addParticipantRequest** | [**AddParticipantRequest**](AddParticipantRequest.md) |  |  |

### Return type

[**AddParticipant200Response**](AddParticipant200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant added |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="addreaction"></a>
# **AddReaction**
> AddReaction200Response AddReaction (string projectId, string chatId, string messageId, AddReactionRequest addReactionRequest)

Add reaction to message


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **messageId** | **string** |  |  |
| **addReactionRequest** | [**AddReactionRequest**](AddReactionRequest.md) |  |  |

### Return type

[**AddReaction200Response**](AddReaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction added |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="createchat"></a>
# **CreateChat**
> CreateChat201Response CreateChat (string projectId, CreateChatRequest createChatRequest)

Create new chat


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **createChatRequest** | [**CreateChatRequest**](CreateChatRequest.md) |  |  |

### Return type

[**CreateChat201Response**](CreateChat201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Chat created |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="deletemessage"></a>
# **DeleteMessage**
> MessageResponse DeleteMessage (string projectId, string chatId, string messageId)

Delete message


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **messageId** | **string** |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message deleted |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="editmessage"></a>
# **EditMessage**
> EditMessage200Response EditMessage (string projectId, string chatId, string messageId, EditMessageRequest editMessageRequest)

Edit message


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **messageId** | **string** |  |  |
| **editMessageRequest** | [**EditMessageRequest**](EditMessageRequest.md) |  |  |

### Return type

[**EditMessage200Response**](EditMessage200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Message edited |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getchatdetails"></a>
# **GetChatDetails**
> GetChatDetails200Response GetChatDetails (string projectId, string chatId)

Get chat details


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |

### Return type

[**GetChatDetails200Response**](GetChatDetails200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Chat details |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getchate2eeparticipantkeys"></a>
# **GetChatE2eeParticipantKeys**
> GetChatE2eeParticipantKeys200Response GetChatE2eeParticipantKeys (string projectId, string chatId)

List participant E2EE public keys

Returns registered identity public keys for users in this chat (for client-side key distribution).


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |

### Return type

[**GetChatE2eeParticipantKeys200Response**](GetChatE2eeParticipantKeys200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant keys |  -  |
| **401** | Authentication required |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getchatmessages"></a>
# **GetChatMessages**
> GetChatMessages200Response GetChatMessages (string projectId, string chatId, int page = null, int limit = null, DateTime before = null, DateTime after = null)

Get chat messages


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 50] |
| **before** | **DateTime** |  | [optional]  |
| **after** | **DateTime** |  | [optional]  |

### Return type

[**GetChatMessages200Response**](GetChatMessages200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages list |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getuserchats"></a>
# **GetUserChats**
> GetUserChats200Response GetUserChats (string projectId, int page = null, int limit = null)

Get user chats


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **page** | **int** |  | [optional] [default to 1] |
| **limit** | **int** |  | [optional] [default to 20] |

### Return type

[**GetUserChats200Response**](GetUserChats200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | User chats list |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="markmessagesasread"></a>
# **MarkMessagesAsRead**
> MarkMessagesAsRead200Response MarkMessagesAsRead (string projectId, string chatId, MarkMessagesAsReadRequest markMessagesAsReadRequest)

Mark messages as read


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **markMessagesAsReadRequest** | [**MarkMessagesAsReadRequest**](MarkMessagesAsReadRequest.md) |  |  |

### Return type

[**MarkMessagesAsRead200Response**](MarkMessagesAsRead200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Messages marked as read |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="putchate2eekey"></a>
# **PutChatE2eeKey**
> PutChatE2eeKey200Response PutChatE2eeKey (string projectId, PutChatE2eeKeyRequest putChatE2eeKeyRequest)

Register chat E2EE identity public key

Stores your long-term public key for end-to-end encrypted chat (key agreement). Private keys never leave the client. Required for other participants to encrypt to you. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **putChatE2eeKeyRequest** | [**PutChatE2eeKeyRequest**](PutChatE2eeKeyRequest.md) |  |  |

### Return type

[**PutChatE2eeKey200Response**](PutChatE2eeKey200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Key saved |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="removeparticipant"></a>
# **RemoveParticipant**
> MessageResponse RemoveParticipant (string projectId, string chatId, RemoveParticipantRequest removeParticipantRequest)

Remove participant from chat


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **removeParticipantRequest** | [**RemoveParticipantRequest**](RemoveParticipantRequest.md) |  |  |

### Return type

[**MessageResponse**](MessageResponse.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Participant removed |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="removereaction"></a>
# **RemoveReaction**
> RemoveReaction200Response RemoveReaction (string projectId, string chatId, string messageId, AddReactionRequest addReactionRequest)

Remove reaction from message


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **messageId** | **string** |  |  |
| **addReactionRequest** | [**AddReactionRequest**](AddReactionRequest.md) |  |  |

### Return type

[**RemoveReaction200Response**](RemoveReaction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Reaction removed |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="sendmessage"></a>
# **SendMessage**
> SendMessage201Response SendMessage (string projectId, string chatId, SendMessageRequest sendMessageRequest)

Send message


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **chatId** | **string** |  |  |
| **sendMessageRequest** | [**SendMessageRequest**](SendMessageRequest.md) |  |  |

### Return type

[**SendMessage201Response**](SendMessage201Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Message sent |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

