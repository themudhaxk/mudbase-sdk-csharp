# Mudbase.SDK.Api.EmailApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**EnqueueProjectEmail**](EmailApi.md#enqueueprojectemail) | **POST** /api/projects/{projectId}/email/send | Enqueue project email (worker delivery) |
| [**GetProjectEmailAnalytics**](EmailApi.md#getprojectemailanalytics) | **GET** /api/projects/{projectId}/analytics/email | Email analytics for a project |
| [**GetProjectEmailSmtp**](EmailApi.md#getprojectemailsmtp) | **GET** /api/projects/{projectId}/email/smtp | Get project SMTP settings (masked) |
| [**GetProjectEmailTemplate**](EmailApi.md#getprojectemailtemplate) | **GET** /api/projects/{projectId}/email/templates/{name} | Get one email template (effective content) |
| [**ListProjectEmailTemplates**](EmailApi.md#listprojectemailtemplates) | **GET** /api/projects/{projectId}/email/templates | List email templates (full catalog for the project) |
| [**PatchProjectEmailSmtp**](EmailApi.md#patchprojectemailsmtp) | **PATCH** /api/projects/{projectId}/email/smtp | Update project SMTP relay (BYO) |
| [**PreviewProjectEmailTemplate**](EmailApi.md#previewprojectemailtemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/preview | Render template preview (sanitized HTML, no send) |
| [**RestoreDefaultProjectEmailTemplate**](EmailApi.md#restoredefaultprojectemailtemplate) | **POST** /api/projects/{projectId}/email/templates/{name}/restore-default | Restore from platform global default or remove project override |
| [**TestProjectEmailSmtp**](EmailApi.md#testprojectemailsmtp) | **POST** /api/projects/{projectId}/email/smtp/test | Verify SMTP and send a test message |
| [**UpsertProjectEmailTemplate**](EmailApi.md#upsertprojectemailtemplate) | **PUT** /api/projects/{projectId}/email/templates/{name} | Upsert project email template (HTML sanitized; variables must cover {{placeholders}}) |
| [**VerifyProjectEmailSmtpDomain**](EmailApi.md#verifyprojectemailsmtpdomain) | **POST** /api/projects/{projectId}/email/smtp/verify-domain | Check DNS (MX + SPF) for sending domain |

<a id="enqueueprojectemail"></a>
# **EnqueueProjectEmail**
> EnqueueProjectEmail202Response EnqueueProjectEmail (string projectId, ProjectEmailSendRequest projectEmailSendRequest)

Enqueue project email (worker delivery)

Queues a transactional email for sending through the email worker and configured provider (platform or per-project SMTP). Provide either `template` (with `data`) or both `subject` and `html`. Returns **202** with `jobId` when accepted. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **projectEmailSendRequest** | [**ProjectEmailSendRequest**](ProjectEmailSendRequest.md) |  |  |

### Return type

[**EnqueueProjectEmail202Response**](EnqueueProjectEmail202Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **202** | Job accepted |  -  |
| **400** | Bad request |  -  |
| **503** | Email queue unavailable |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectemailanalytics"></a>
# **GetProjectEmailAnalytics**
> GetProjectEmailAnalytics200Response GetProjectEmailAnalytics (string projectId, DateTime from = null, DateTime to = null)

Email analytics for a project

Aggregated email log stats for the project. Optional `from` and `to` query params filter by date range (ISO 8601). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **from** | **DateTime** |  | [optional]  |
| **to** | **DateTime** |  | [optional]  |

### Return type

[**GetProjectEmailAnalytics200Response**](GetProjectEmailAnalytics200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Analytics payload |  -  |
| **401** | Authentication required |  -  |
| **403** | Access denied |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectemailsmtp"></a>
# **GetProjectEmailSmtp**
> GetProjectEmailSmtp200Response GetProjectEmailSmtp (string projectId)

Get project SMTP settings (masked)


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**GetProjectEmailSmtp200Response**](GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | SMTP configuration without secrets |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getprojectemailtemplate"></a>
# **GetProjectEmailTemplate**
> GetProjectEmailTemplate200Response GetProjectEmailTemplate (string projectId, string name)

Get one email template (effective content)

Returns the template body that would be used when sending: project override if present, else global default, else built-in fallback. **`isProjectOverride`** is true only when this project has a stored row; **`effectiveSource`** is `project`, `global`, or `builtin`. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **name** | **string** |  |  |

### Return type

[**GetProjectEmailTemplate200Response**](GetProjectEmailTemplate200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Template document (resolved for send) |  -  |
| **404** | Resource not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="listprojectemailtemplates"></a>
# **ListProjectEmailTemplates**
> ListProjectEmailTemplates200Response ListProjectEmailTemplates (string projectId)

List email templates (full catalog for the project)

Returns every template name the worker can resolve for this project: **built-in** defaults, **global** platform rows (`project: null` in DB), and **project** overrides. Use **`isCustomized`** to see if this project has its own stored copy; **`effectiveSource`** shows which layer would be used at send time (`project` wins over `global` over `builtin`). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |

### Return type

[**ListProjectEmailTemplates200Response**](ListProjectEmailTemplates200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Template catalog with customization flags |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="patchprojectemailsmtp"></a>
# **PatchProjectEmailSmtp**
> GetProjectEmailSmtp200Response PatchProjectEmailSmtp (string projectId, ProjectSmtpPatchRequest projectSmtpPatchRequest)

Update project SMTP relay (BYO)

Set `authPass` in the body to store an encrypted password (never returned on GET). Validates host/user when enabling. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **projectSmtpPatchRequest** | [**ProjectSmtpPatchRequest**](ProjectSmtpPatchRequest.md) |  |  |

### Return type

[**GetProjectEmailSmtp200Response**](GetProjectEmailSmtp200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Updated settings (masked) |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="previewprojectemailtemplate"></a>
# **PreviewProjectEmailTemplate**
> void PreviewProjectEmailTemplate (string projectId, string name, PreviewProjectEmailTemplateRequest previewProjectEmailTemplateRequest = null)

Render template preview (sanitized HTML, no send)

Body **`sampleData`** is merged with layout defaults; keys should match `{{placeholders}}` in the template (see **Email** tag for the catalog). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **name** | **string** |  |  |
| **previewProjectEmailTemplateRequest** | [**PreviewProjectEmailTemplateRequest**](PreviewProjectEmailTemplateRequest.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Rendered subject and HTML |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="restoredefaultprojectemailtemplate"></a>
# **RestoreDefaultProjectEmailTemplate**
> void RestoreDefaultProjectEmailTemplate (string projectId, string name)

Restore from platform global default or remove project override


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **name** | **string** |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Restored or deleted override |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="testprojectemailsmtp"></a>
# **TestProjectEmailSmtp**
> DeleteFunction200Response TestProjectEmailSmtp (string projectId, ProjectSmtpTestRequest projectSmtpTestRequest)

Verify SMTP and send a test message

Rate-limited. With `useSaved: true` (default), uses stored credentials; otherwise pass `host`, `authUser`, `authPass`, etc. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **projectSmtpTestRequest** | [**ProjectSmtpTestRequest**](ProjectSmtpTestRequest.md) |  |  |

### Return type

[**DeleteFunction200Response**](DeleteFunction200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | SMTP verified and test mail sent |  -  |
| **400** | Bad request |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="upsertprojectemailtemplate"></a>
# **UpsertProjectEmailTemplate**
> void UpsertProjectEmailTemplate (string projectId, string name, UpsertProjectEmailTemplateRequest upsertProjectEmailTemplateRequest)

Upsert project email template (HTML sanitized; variables must cover {{placeholders}})

Saves a **project override** for `name`. HTML is sanitized. **`variables`** must list every `{{token}}` used in `subject`, `htmlBody`, and `textBody` (see **Email** tag description for the full placeholder catalog). 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **name** | **string** |  |  |
| **upsertProjectEmailTemplateRequest** | [**UpsertProjectEmailTemplateRequest**](UpsertProjectEmailTemplateRequest.md) |  |  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Saved template |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="verifyprojectemailsmtpdomain"></a>
# **VerifyProjectEmailSmtpDomain**
> void VerifyProjectEmailSmtpDomain (string projectId, VerifyProjectEmailSmtpDomainRequest verifyProjectEmailSmtpDomainRequest = null)

Check DNS (MX + SPF) for sending domain

Resolves the domain from `domain`, `fromEmail`, or saved `emailSmtp.fromEmail`. Returns whether MX and SPF TXT exist. With `persist: true` and checks passed, sets `emailSmtp.domainVerifiedAt`. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **verifyProjectEmailSmtpDomainRequest** | [**VerifyProjectEmailSmtpDomainRequest**](VerifyProjectEmailSmtpDomainRequest.md) |  | [optional]  |

### Return type

void (empty response body)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | DNS check result |  -  |
| **400** | Bad request |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

