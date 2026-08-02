# Mudbase.SDK.Api.AddOnsApi

All URIs are relative to *https://cloud.mudbase.dev*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**ApiAddonsGet**](AddOnsApi.md#apiaddonsget) | **GET** /api/addons | List the add-on catalog |
| [**ApiProjectsProjectIdAddonsAddonInvokePost**](AddOnsApi.md#apiprojectsprojectidaddonsaddoninvokepost) | **POST** /api/projects/{projectId}/addons/{addon}/invoke | Invoke an add-on for a project |
| [**ApiProjectsProjectIdAddonsJobsIdGet**](AddOnsApi.md#apiprojectsprojectidaddonsjobsidget) | **GET** /api/projects/{projectId}/addons/jobs/{id} | Get an add-on job status |

<a id="apiaddonsget"></a>
# **ApiAddonsGet**
> ApiAddonsGet200Response ApiAddonsGet ()

List the add-on catalog

Returns the available add-ons (key, metadata, pricing) the caller can invoke.


### Parameters
This endpoint does not need any parameter.
### Return type

[**ApiAddonsGet200Response**](ApiAddonsGet200Response.md)

### Authorization

[OrgBearerAuth](../README.md#OrgBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on catalog |  -  |
| **401** | Authentication required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apiprojectsprojectidaddonsaddoninvokepost"></a>
# **ApiProjectsProjectIdAddonsAddonInvokePost**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response ApiProjectsProjectIdAddonsAddonInvokePost (string projectId, string addon, Object body = null)

Invoke an add-on for a project

Runs the named add-on against the project. Returns the job synchronously (200) when it completes immediately, or 202 with a pending job when processing continues in the background.


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **addon** | **string** | Add-on key from the catalog. |  |
| **body** | **Object** |  | [optional]  |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Add-on job completed |  -  |
| **202** | Add-on job accepted and processing |  -  |
| **400** | Invalid add-on key or input |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

<a id="apiprojectsprojectidaddonsjobsidget"></a>
# **ApiProjectsProjectIdAddonsJobsIdGet**
> ApiProjectsProjectIdAddonsAddonInvokePost200Response ApiProjectsProjectIdAddonsJobsIdGet (string projectId, string id)

Get an add-on job status


### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **projectId** | **string** |  |  |
| **id** | **string** | Add-on job id. |  |

### Return type

[**ApiProjectsProjectIdAddonsAddonInvokePost200Response**](ApiProjectsProjectIdAddonsAddonInvokePost200Response.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth), [ProjectBearerAuth](../README.md#ProjectBearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | The add-on job |  -  |
| **401** | Authentication required |  -  |
| **403** | Project ownership required |  -  |
| **404** | Add-on job not found |  -  |

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

