# WebCookieManager

WebCookieManager is the cookie manager for Web components, providing global management capabilities for cookies in Web components. With this class, developers can obtain, set, save, and clear cookies, as well as control cookie permissions. All methods of this class are static, and all Web components in an app share a single WebCookieManager instance. The cookie format complies with the [RFC6265](https://www.rfc-editor.org/info/rfc6265/) standard.

When browsing web pages in Privacy Mode, data such as cookies and caches are not written to local persistent storage. After the Web component in Privacy Mode is destroyed, this data is cleared and not retained.

> **NOTE:** 
> 
> - Static methods must be used on the user interface (UI) thread.

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## clearAllCookies

```TypeScript
static clearAllCookies(): Promise<void>
```

Clears all cookies, including session cookies and persistent cookies. This API uses a promise to return the result. To clear only session cookies, use [clearSessionCookie](#clearsessioncookie).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

## clearAllCookies

```TypeScript
static clearAllCookies(callback: AsyncCallback<void>): void
```

Clears all cookies, including session cookies and persistent cookies. This API uses an asynchronous callback to return the result. To clear only session cookies, use [clearSessionCookie](#clearsessioncookie-1).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result, indicating whether all cookies are cleared successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## clearAllCookiesSync

```TypeScript
static clearAllCookiesSync(incognito?: boolean): void
```

Clears all cookies, including session cookies and persistent cookies. To clear only session cookies, use [clearSessionCookieSync](#clearsessioncookiesync).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| incognito | boolean | No | Whether to clear all cookies in incognito mode. The value **true** means to clear all cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**. <br>If **undefined** or **null** is passed, cookies are not cleared. |

## clearSessionCookie

```TypeScript
static clearSessionCookie(): Promise<void>
```

Clears all session cookies. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

## clearSessionCookie

```TypeScript
static clearSessionCookie(callback: AsyncCallback<void>): void
```

Clears all session cookies. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function used to return whether all session cookies are cleared successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## clearSessionCookieSync

```TypeScript
static clearSessionCookieSync(): void
```

Deletes all session cookies.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## configCookie

```TypeScript
static configCookie(url: string, value: string): Promise<void>
```

Sets a single cookie value for a specified URL. This API uses a promise to return the result.

> **NOTE:** 
> 
> - In configCookie, you can specify a domain name in the URL so that in-page requests also carry the cookie.
> 
> - Cookies are periodically saved to the disk every 30 seconds. You can also use [saveCookieAsync](#savecookieasync-1) for force storage.
> 
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", optionally followed by a cookie property list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If a cookie with the same host, path, and name exists, it will be replaced by the new cookie. If the cookie to set has expired, it will not be stored. To set multiple cookies, call this method multiple times.
> 
> - If configCookie is called twice or more to set cookies, each cookie set is separated by "; ".
> 
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
> 
> - To overwrite HttpOnly cookies, specify the HttpOnly attribute in the value.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to set. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## configCookie

```TypeScript
static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>
```

Sets a single cookie value for a specified URL. This API uses a promise to return the result.

> **NOTE:** 
> 
> - In configCookie, you can specify a domain name in the URL so that in-page requests also carry the cookie.
> 
> - Cookies are periodically saved to the disk every 30 seconds. You can also use [saveCookieAsync](#savecookieasync-1) for force storage.
> 
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", optionally followed by a cookie property list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If a cookie with the same host, path, and name exists, it will be replaced by the new cookie. If the cookie to set has expired, it will not be stored. To set multiple cookies, call this method multiple times.
> 
> - If configCookie is called twice or more to set cookies, each cookie set is separated by "; ".
> 
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL to which the cookie to set belongs. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |
| incognito | boolean | Yes | Whether to set the cookies in incognito mode. The value **true** means to set the cookies in incognito mode, and **false** means the opposite. |
| includeHttpOnly | boolean | Yes | Whether to overwrite cookies containing **HttpOnly**. The value **true** means to overwrite cookies containing **HttpOnly**, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## configCookie

```TypeScript
static configCookie(url: string, value: string, callback: AsyncCallback<void>): void
```

Sets a single cookie value for a specified URL. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> - In configCookie, you can specify a domain name in the URL so that in-page requests also carry the cookie.
> 
> - Cookies are periodically saved to the disk every 30 seconds. You can also use [saveCookieAsync](#savecookieasync-1) for force storage.
> 
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", optionally followed by a cookie property list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If a cookie with the same host, path, and name exists, it will be replaced by the new cookie. If the cookie to set has expired, it will not be stored. To set multiple cookies, call this method multiple times.
> 
> - If configCookie is called twice or more to set cookies, each cookie set is separated by "; ".
> 
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
> 
> - To overwrite HttpOnly cookies, specify the HttpOnly attribute in the value.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to set. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result of setting the cookie. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito?: boolean): void
```

Sets a cookie for the specified URL.

> **NOTE:** 
> 
> - In configCookieSync, you can specify a domain name in the URL so that in-page requests also carry the cookie.
> 
> - Cookies are periodically saved to the disk every 30 seconds. You can also use [saveCookieAsync](#savecookieasync-1) for force storage.
> 
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", optionally followed by a cookie property list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If a cookie with the same host, path, and name exists, it will be replaced by the new cookie. If the cookie to set has expired, it will not be stored. To set multiple cookies, call this method multiple times.
> 
> - If configCookieSync is called twice or more to set cookies, each cookie set is separated by "; ".
> 
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.
> 
> - To overwrite HttpOnly cookies, specify the HttpOnly attribute in the value.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to set. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |
| incognito | boolean | No | Whether to set the cookies in incognito mode. The value **true** means to set the cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**. <br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void
```

Sets a single cookie value for a specified URL.

> **NOTE:** 
> 
> - In configCookieSync, you can specify a domain name in the URL so that in-page requests also carry the cookie.
> 
> - Cookies are periodically saved to the disk every 30 seconds. You can also use [saveCookieAsync](#savecookieasync-1) for force storage.
> 
> - The value parameter must follow the format of the Set-Cookie HTTP response header. It is a key-value pair in the form of "key=value", optionally followed by a cookie property list separated by "; " (for example, "key=value; Max-Age=100").
> 
> - If a cookie with the same host, path, and name exists, it will be replaced by the new cookie. If the cookie to set has expired, it will not be stored. To set multiple cookies, call this method multiple times.
> 
> - If configCookieSync is called twice or more to set cookies, each cookie set is separated by "; ".
> 
> - If the specified value contains the "Secure" attribute, the URL must use the "https://" protocol.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to set. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |
| incognito | boolean | Yes | Whether to set the cookies in incognito mode. The value **true** means to set the cookies in incognito mode, and **false** means the opposite. |
| includeHttpOnly | boolean | Yes | Whether to overwrite cookies containing **HttpOnly**. The value **true** means to overwrite cookies containing **HttpOnly**, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## deleteEntireCookie

```TypeScript
static deleteEntireCookie(): void
```

Deletes all cookies.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [clearAllCookiesSync](#clearallcookiessync)

**System capability:** SystemCapability.Web.Webview.Core

## deleteSessionCookie

```TypeScript
static deleteSessionCookie(): void
```

Deletes all session cookies.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [clearSessionCookieSync](#clearsessioncookiesync)

**System capability:** SystemCapability.Web.Webview.Core

## existCookie

```TypeScript
static existCookie(incognito?: boolean): boolean
```

Checks whether cookies exist.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| incognito | boolean | No | Whether to check for cookies in incognito mode. The value **true** means to check for cookies in incognito mode, and **false** means the opposite.<br>The default value is **false**. <br>If **undefined** or **null** is passed, **undefined** is returned.<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether cookies exist. The value **true** means that cookies exist, and **false** means the opposite. |

## fetchAllCookies

```TypeScript
static fetchAllCookies(incognito: boolean): Promise<Array<WebHttpCookie>>
```

Obtains all cookies. This API uses a promise to return the result.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| incognito | boolean | Yes | `true` Gets all cookies in incognito context; `false` otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WebHttpCookie](arkts-arkweb-webview-webhttpcookie-i.md)&gt;&gt; | Promise used to obtain all cookies and their corresponding field values. |

## fetchCookie

```TypeScript
static fetchCookie(url: string): Promise<string>
```

Obtains the cookie value of a specified URL. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for which the cookie is to be obtained. It is recommended to use a complete URL. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## fetchCookie

```TypeScript
static fetchCookie(url: string, incognito: boolean): Promise<string>
```

Obtains the cookie value of a specified URL. This API uses a promise to return the result.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for which the cookie is to be obtained. A complete URL is recommended. |
| incognito | boolean | Yes | Whether to obtain the cookie in incognito mode. The value **true** means to obtain the cookie in incognito mode, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## fetchCookie

```TypeScript
static fetchCookie(url: string, incognito: boolean, includePartitionedCookies: boolean): Promise<string>
```

Obtains the cookies corresponding to a specified URL. The parameter incognito specifies whether to obtain cookies in Privacy Mode, and the parameter includePartitionedCookies specifies whether to obtain first-party partitioned cookies. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to obtain. A complete URL is recommended. |
| incognito | boolean | Yes | Whether to obtain the in-memory cookies of the Web component in Privacy Mode. The value **true** indicates Privacy Mode, and **false** indicates Non-Privacy Mode.<br>Passing **undefined** or **null** throws error code 401. |
| includePartitionedCookies | boolean | Yes | Whether to allow obtaining first-party partitioned cookies. The value **true** indicates that first-party partitioned cookies are allowed, and **false** indicates that they are not allowed.<br>Passing **undefined** or **null** throws error code 401. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to obtain the cookies corresponding to the specified URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## fetchCookie

```TypeScript
static fetchCookie(url: string, callback: AsyncCallback<string>): void
```

Obtains the cookie value of a specified URL. This API uses an asynchronous callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for which the cookie is to be obtained. A complete URL is recommended. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to obtain the cookie. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## fetchCookieSync

```TypeScript
static fetchCookieSync(url: string, incognito?: boolean): string
```

Obtains the cookie value of the specified URL.

> **NOTE:** 
> 
> - The system automatically deletes expired cookies. For data with the same key name, the new data overwrites the previous data.
> 
> - To obtain a usable cookie value, you are advised to pass a complete URL to fetchCookieSync.
> 
> - fetchCookieSync is used to obtain all cookie values. Each cookie value is separated by "; ", but a specific cookie value cannot be obtained individually.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for which the cookie is to be obtained. A complete URL is recommended. |
| incognito | boolean | No | Whether to obtain the cookie in incognito mode. The value **true** means to obtain the cookie in incognito mode, and **false** means the opposite.<br>The default value is **false**. <br>If **undefined** or **null** is passed, error code **401** will be thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Cookie value corresponding to the specified URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## fetchCookieSync

```TypeScript
static fetchCookieSync(url: string, incognito?: boolean, includePartitionedCookies?: boolean): string
```

Obtains the cookies corresponding to a specified URL. The optional parameter incognito specifies whether to obtain cookies in Privacy Mode, and the optional parameter includePartitionedCookies specifies whether to obtain first-party partitioned cookies.

> **NOTE:** 
> 
> - The system automatically deletes expired cookies. For data with the same key name, the new data overwrites the previous data.
> 
> - To obtain a usable cookie value, you are advised to pass a complete URL to fetchCookieSync.
> 
> - fetchCookieSync is used to obtain all cookie values. Each cookie value is separated by "; ", but a specific cookie value cannot be obtained individually.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to obtain. A complete URL is recommended. |
| incognito | boolean | No | Whether to obtain the in-memory cookies of the Web component in Privacy Mode. The value **true** indicates Privacy Mode, and **false** indicates Non-Privacy Mode.<br>Default value: **false**. <br>Passing **undefined** or **null** throws error code 401. |
| includePartitionedCookies | boolean | No | Whether to allow obtaining first-party partitioned cookies. The value **true** indicates that first-party partitioned cookies are allowed, and **false** indicates that they are not allowed.<br>Default value: **false**. <br>Passing **undefined** or **null** throws error code 401. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Cookies corresponding to the specified URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## getCookie

```TypeScript
static getCookie(url: string): string
```

Obtains the cookie value of the specified URL.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [fetchCookieSync](#fetchcookiesync)

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for which the cookie is to be obtained. A complete URL is recommended. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Cookie value corresponding to the specified URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |

## isCookieAllowed

```TypeScript
static isCookieAllowed(): boolean
```

Checks whether the **WebCookieManager** instance has the permission to send and receive cookies.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the **WebCookieManager** instance has the permission to send and receive cookies.<br>The value **true** indicates that the **WebCookieManager** instance has the permission to send and receive cookies, and **false** indicates the opposite. <br>Default value: **true**. |

## isThirdPartyCookieAllowed

```TypeScript
static isThirdPartyCookieAllowed(): boolean
```

Checks whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.<br>The value **true** indicates that the **WebCookieManager** instance has the permission to send and receive third-party cookies, and **false** indicates the opposite. <br>The default value is **false**. |

## putAcceptCookieEnabled

```TypeScript
static putAcceptCookieEnabled(accept: boolean): void
```

Sets whether the **WebCookieManager** instance has the permission to send and receive cookies.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accept | boolean | Yes | Whether to have the permission to send and receive cookies. The default value is **true**, indicating that the app has the permission to send and receive cookies. The value **false** indicates that the app does not have the permission to send and receive cookies. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## putAcceptThirdPartyCookieEnabled

```TypeScript
static putAcceptThirdPartyCookieEnabled(accept: boolean): void
```

Sets whether the **WebCookieManager** instance has the permission to send and receive third-party cookies.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accept | boolean | Yes | Whether to allow sending and receiving third-party cookies.<br>The value **true** means allowed, and **false** means not allowed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieAsync

```TypeScript
static saveCookieAsync(): Promise<void>
```

Saves all cookies that can be obtained through fetchCookie and need to be persisted to the disk. This API uses a promise to return the result.

> **NOTE:** 
> 
> - saveCookieAsync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieAsync is called, session cookies are not written to the disk.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieAsync

```TypeScript
static saveCookieAsync(callback: AsyncCallback<void>): void
```

Asynchronously saves all cookies (that can be obtained through **fetchCookie** and need to be persisted) to the disk.

> **NOTE:** 
> 
> - saveCookieAsync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieAsync is called, session cookies are not written to the disk.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to indicate whether the cookie is saved successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieSync

```TypeScript
static saveCookieSync(): void
```

Synchronously saves all cookies (that can be obtained through **fetchCookie** and need to be persisted) to the disk.

> **NOTE:** 
> 
> - saveCookieSync is used to forcibly write cookies that need to be persisted to the disk. Session cookies are not persisted on PC/2-in-1 and tablet devices. Even if saveCookieSync is called, session cookies are not written to the disk.
> 
> - saveCookieSync blocks the caller until the operation is complete, during which I/O operations may be performed.

**Since:** 15

**System capability:** SystemCapability.Web.Webview.Core

## setCookie

```TypeScript
static setCookie(url: string, value: string): void
```

Sets a cookie for the specified URL.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [configCookieSync](#configcookiesync)

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL of the cookie to set. A complete URL is recommended. |
| value | string | Yes | Cookie value to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-incorrect-url-format) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-invalid-cookie-value) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

## setLazyInitializeWebEngine

```TypeScript
static setLazyInitializeWebEngine(lazy: boolean): void
```

Sets whether to delay the initialization of the ArkWeb kernel. If this method is not called, the ArkWeb kernel is not delayed by default.

> **NOTE:** 
> 
> - This API is a global static method. It must be called before using ArkWeb components and initializing the ArkWeb kernel. Otherwise, the setting does not take effect.
> 
> - This API applies only to APIs that initialize CookieManager when called, such as other APIs of this class WebCookieManager. After this API is called and set to **true**, calling applicable APIs skips the initialization of the ArkWeb kernel when initializing CookieManager. You need to initialize the ArkWeb kernel separately afterwards.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lazy | boolean | Yes | Controls whether to delay the initialization of the web engine. |
