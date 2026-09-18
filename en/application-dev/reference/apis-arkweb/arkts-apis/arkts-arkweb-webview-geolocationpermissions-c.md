# GeolocationPermissions

GeolocationPermissions is the geolocation permission management object for the Web component. It provides management capabilities such as querying, authorizing, and deleting saved geolocation permission statuses in the Web component. With GeolocationPermissions, an app can pre-authorize access for a specific origin before a web page initiates a geolocation request, and can also proactively query or clear saved permission records without relying on the pop-up authorization flow when a web page requests permission.

GeolocationPermissions is suitable for scenarios where proactive management of Web component geolocation permissions is required. For example, an app may want to pre-authorize trusted websites to access geolocation, avoiding authorization prompts on each visit; or an app may need to clear geolocation permission records that are no longer needed by the user. The following permissions are required for accessing geolocation: ohos.permission.LOCATION, ohos.permission.APPROXIMATELY_LOCATION, and ohos.permission.LOCATION_IN_BACKGROUND. For details about the permissions, see [Development Guide for Location Permission Application](../../../device/location/location-permission-guidelines.md).

> **NOTE:** 
> 
> - You must load the **Web** component before calling the APIs in **GeolocationPermissions**.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## allowGeolocation

```TypeScript
static allowGeolocation(origin: string, incognito?: boolean): void
```

Allows the specified origin to use the geolocation APIs. It is used to pre-authorize geolocation permission for trusted websites to avoid repeated pop-ups, or to allow an app to proactively manage the geolocation authorization of a specific origin.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a string that does not comply with the RFC 6454 format is input, with error code 17100011. |
| incognito | boolean | No | The value **true** indicates that the specified origin is allowed to use geolocation in privacy mode, and **false** indicates that the specified origin is allowed to use geolocation in normal (non-privacy) mode.<br>Default value: **false**. <br>The value is **false** when null or undefined is input.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-invalid-origin) | Invalid origin. |

## deleteAllGeolocation

```TypeScript
static deleteAllGeolocation(incognito?: boolean): void
```

Clears the geolocation permission status of all origins. It is used to revoke geolocation authorization in batches in scenarios such as user logout or one-click clearing.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| incognito | boolean | No | The value **true** indicates clearing the geolocation permission status of all origins in Privacy Mode, and **false** indicates clearing the geolocation permission status of all origins in Normal Mode.<br>Default value: **false**. <br>The value **false** is used when null or undefined is input.<br>**Since:** 11 |

## deleteGeolocation

```TypeScript
static deleteGeolocation(origin: string, incognito?: boolean): void
```

Clears the geolocation permission status of the specified origin. It is used to revoke the geolocation authorization of a specified website, or to provide an app with the ability to manage permissions by origin.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. Throws an exception when a string that does not comply with the RFC 6454 format is input. Error code: 17100011. |
| incognito | boolean | No | Whether to clear the geolocation permission status of the specified origin in privacy mode. The value **true** indicates clearing in privacy mode, and **false** indicates clearing in normal non-privacy mode.<br>Default value: **false**. <br>The value is **false** when null or undefined is input.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-invalid-origin) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise<boolean>
```

Obtains the geolocation permission status of the specified origin. This API uses a promise to return the result. It is used to query the geolocation authorization result of a specified website, such as displaying the permission status on a settings page or verifying authorization before access.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a string that does not comply with the RFC 6454 format is input, with error code 17100011. |
| incognito | boolean | No | Whether to obtain the geolocation permission status of the specified origin in privacy mode. The value **true** indicates obtaining in privacy mode, and **false** indicates obtaining in normal mode.<br>Default value: **false**. <br>An exception with error code 401 is thrown when null or undefined is input.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the geolocation permission status of the specified origin.<br>If the operation is successful, the value **true** means that the geolocation permission is granted, and **false** means the opposite. <br>If the operation fails, the geolocation permission status of the specified origin is not found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-invalid-origin) | Invalid origin. |

## getAccessibleGeolocation

```TypeScript
static getAccessibleGeolocation(origin: string, callback: AsyncCallback<boolean>, incognito?: boolean): void
```

Obtains the geolocation permission status of the specified origin. This API uses an asynchronous callback to return the result. It is used to query the geolocation authorization result of a specified website, such as displaying the permission status on a settings page or verifying authorization before access.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| origin | string | Yes | String of the specified origin.<br>The origin format must comply with the format defined in RFC 6454. An exception is thrown when a non- conforming input string is input. Error code: 17100011. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the geolocation permission status of the specified origin.<br>If the operation is successful, the value **true** means that the geolocation permission is granted, and **false** means the opposite. <br>If the operation fails, the geolocation permission status of the specified origin is not found. |
| incognito | boolean | No | The value **true** indicates to get the geolocation permission status of the specified origin in privacy mode, and **false** indicates to get it in normal mode.<br>Default value: **false**. <br>Throws an exception error with error code 401 when null or undefined is input.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100011](../errorcode-webview.md#17100011-invalid-origin) | Invalid origin. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(incognito?: boolean): Promise<Array<string>>
```

Obtains the geolocation permission status of all origins. This API uses a promise to return the result. It is used to obtain a list of websites that have been granted geolocation permission, such as displaying on a privacy settings page or batch management on a permission management page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| incognito | boolean | No | The value **true** indicates that all origin information of stored geolocation permission status is obtained in private mode, and **false** indicates that it is obtained in normal mode.<br>Default value: **false**. <br>Throws an exception error code 401 when null or undefined is passed in.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the geolocation permission status of all origins. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## getStoredGeolocation

```TypeScript
static getStoredGeolocation(callback: AsyncCallback<Array<string>>, incognito?: boolean): void
```

Obtains the geolocation permission status of all origins. This API uses an asynchronous callback to return the result. It is used to obtain a list of websites that have been granted geolocation permission, such as displaying on a privacy settings page or batch management on a permission management page.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback invoked to return all origin information of stored geolocation permission statuses. The callback parameters include: error (error object, which is null when retrieval is successful) and origins (array of origin strings with stored geolocation permissions, where each element is an origin string that complies with the format defined in RFC 6454). When retrieval fails, error is the error object. |
| incognito | boolean | No | Whether to obtain all origin information of stored geolocation permission statuses in privacy mode. The value **true** indicates privacy mode, and **false** indicates normal mode.<br>Default value: **false**. <br>Throws an exception error code 401 when null or undefined is passed in.<br>**Since:** 11 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
