# Mudbase.SDK.Api.ComplianceApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiGdprErasePost**](ComplianceApi.md#apigdprerasepost) | **POST** /api/gdpr/erase | Erase my personal data (GDPR Art. 17) |
| [**ApiGdprExportGet**](ComplianceApi.md#apigdprexportget) | **GET** /api/gdpr/export | Export my personal data (GDPR Art. 15) |
| [**GenerateAccessReview**](ComplianceApi.md#generateaccessreview) | **POST** /api/compliance/access-review | Generate access review report (SOC 2) |
| [**GenerateDataProcessingRecord**](ComplianceApi.md#generatedataprocessingrecord) | **POST** /api/compliance/data-processing-record | Generate data processing record (GDPR Article 30) |
| [**GetComplianceSummary**](ComplianceApi.md#getcompliancesummary) | **GET** /api/compliance/summary | Get compliance summary |
| [**LogSecurityEvent**](ComplianceApi.md#logsecurityevent) | **POST** /api/compliance/security-event | Log security event |

<a id="apigdprerasepost"></a>
# **ApiGdprErasePost**
> ApplyRoleFeaturePreset200Response ApiGdprErasePost (ApiGdprErasePostRequest apiGdprErasePostRequest)

Erase my personal data (GDPR Art. 17)

Anonymizes the subject's PII, revokes sessions/tokens, and anonymizes (never hard-deletes) financial/legal-retention records. Idempotent and self-scoped.  Requires re-proving your current password (skipped only for OAuth-only accounts with no password set) and, if 2FA is enabled, a fresh TOTP code - the same step-up re-authentication already required by the less-destructive `PATCH /api/users/password` and `POST /api/users/2fa/disable`. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **apiGdprErasePostRequest** | [**ApiGdprErasePostRequest**](ApiGdprErasePostRequest.md) |  |  |

### Return type

[**ApplyRoleFeaturePreset200Response**](ApplyRoleFeaturePreset200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data anonymized (or already anonymized — idempotent) |  -  |
| **400** | Confirmation field missing/not equal to \&quot;DELETE\&quot;, or currentPassword/totpToken missing or invalid |  -  |
| **401** | Authentication required |  -  |
| **409** | Sole owner of one or more organizations - transfer or delete them first |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apigdprexportget"></a>
# **ApiGdprExportGet**
> Object ApiGdprExportGet ()

Export my personal data (GDPR Art. 15)

Returns the authenticated subject's personal data as a downloadable JSON attachment. Self-scoped — a caller can only export their own data.


### Parameters
This endpoint does not need any parameter.
### Return type

**Object**

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | JSON attachment containing the subject&#39;s personal data |  -  |
| **401** | Authentication required |  -  |
| **429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="generateaccessreview"></a>
# **GenerateAccessReview**
> GenerateAccessReview200Response GenerateAccessReview (GenerateAccessReviewRequest generateAccessReviewRequest)

Generate access review report (SOC 2)

Generate access review report for compliance audits (SOC 2, ISO 27001, etc.). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations. 


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **generateAccessReviewRequest** | [**GenerateAccessReviewRequest**](GenerateAccessReviewRequest.md) |  |  |

### Return type

[**GenerateAccessReview200Response**](GenerateAccessReview200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Access review report generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="generatedataprocessingrecord"></a>
# **GenerateDataProcessingRecord**
> GenerateDataProcessingRecord200Response GenerateDataProcessingRecord (GenerateDataProcessingRecordRequest generateDataProcessingRecordRequest)

Generate data processing record (GDPR Article 30)

Generate GDPR Article 30 compliant data processing record


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **generateDataProcessingRecordRequest** | [**GenerateDataProcessingRecordRequest**](GenerateDataProcessingRecordRequest.md) |  |  |

### Return type

[**GenerateDataProcessingRecord200Response**](GenerateDataProcessingRecord200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Data processing record generated |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="getcompliancesummary"></a>
# **GetComplianceSummary**
> GetComplianceSummary200Response GetComplianceSummary ()

Get compliance summary

Get compliance dashboard data (GDPR, SOC 2, security status). Requires JWT Bearer token authentication. Both OrgBearerAuth and ProjectBearerAuth are supported (they use the same JWT token format). These are organization-level operations.


### Parameters
This endpoint does not need any parameter.
### Return type

[**GetComplianceSummary200Response**](GetComplianceSummary200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Compliance summary |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="logsecurityevent"></a>
# **LogSecurityEvent**
> LogSecurityEvent200Response LogSecurityEvent (LogSecurityEventRequest logSecurityEventRequest)

Log security event

Log a security event for compliance and audit purposes


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **logSecurityEventRequest** | [**LogSecurityEventRequest**](LogSecurityEventRequest.md) |  |  |

### Return type

[**LogSecurityEvent200Response**](LogSecurityEvent200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Security event logged |  -  |
| **400** | Bad request |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

