# Mudbase.SDK.Api.ComplianceApi

All URIs are relative to *https://cloud.dev.mudbase*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ComplianceLogSecurityEvent**](ComplianceApi.md#compliancelogsecurityevent) | **POST** /api/compliance/security-event | Log security event |

<a id="compliancelogsecurityevent"></a>
# **ComplianceLogSecurityEvent**
> ComplianceLogSecurityEvent200Response ComplianceLogSecurityEvent (ComplianceLogSecurityEventRequest complianceLogSecurityEventRequest)

Log security event

Log a security event for compliance and audit (e.g. SOC 2, GDPR). Event type and severity are required; optional details (userId, resource, ipAddress, etc.) for forensics.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **complianceLogSecurityEventRequest** | [**ComplianceLogSecurityEventRequest**](ComplianceLogSecurityEventRequest.md) | Event type (e.g. unauthorized_access_attempt, brute_force_attempt), severity (low–critical), and optional details object for context. |  |

### Return type

[**ComplianceLogSecurityEvent200Response**](ComplianceLogSecurityEvent200Response.md)

### Authorization

[BearerToken](../README.md#BearerToken)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Security event logged |  -  |
| **400** | Bad request or validation error. The **error** field contains the exact backend message, e.g. \&quot;Validation failed\&quot;, \&quot;projectId is required\&quot;, \&quot;No file provided\&quot;, \&quot;Invalid project ID format\&quot;. **details** may contain validation errors when present.  |  -  |
| **401** | Not authenticated. The **error** field contains the exact backend message, e.g. \&quot;Invalid token.\&quot;, \&quot;Access denied. No token provided.\&quot;, \&quot;Authentication required\&quot;, \&quot;Invalid API key\&quot;, \&quot;API key expired\&quot;.  |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

