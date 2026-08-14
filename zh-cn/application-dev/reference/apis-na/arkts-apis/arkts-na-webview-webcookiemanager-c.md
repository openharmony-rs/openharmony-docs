# WebCookieManager

Provides methods for managing the web cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebCookieManager--><!--Device-webview-class WebCookieManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearAllCookies

```TypeScript
static clearAllCookies(): Promise<void>
```

Remove all cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearAllCookies(): Promise<void>--><!--Device-WebCookieManager-static clearAllCookies(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A promise resolved after the cookies have been deleted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

## clearAllCookies

```TypeScript
static clearAllCookies(callback: AsyncCallback<void>): void
```

Remove all cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearAllCookies(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static clearAllCookies(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Called after the cookies have been deleted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## clearAllCookiesSync

```TypeScript
static clearAllCookiesSync(incognito?: boolean): void
```

Remove all cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearAllCookiesSync(incognito?: boolean): void--><!--Device-WebCookieManager-static clearAllCookiesSync(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | {@code true} remove all cookies in incognito mode; {@code false} otherwise. |

## clearSessionCookie

```TypeScript
static clearSessionCookie(): Promise<void>
```

Delete the session cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearSessionCookie(): Promise<void>--><!--Device-WebCookieManager-static clearSessionCookie(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A promise resolved after the cookies have been deleted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

## clearSessionCookie

```TypeScript
static clearSessionCookie(callback: AsyncCallback<void>): void
```

Delete the session cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearSessionCookie(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static clearSessionCookie(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Called after the cookies have been deleted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |

## clearSessionCookieSync

```TypeScript
static clearSessionCookieSync(): void
```

Delete the session cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static clearSessionCookieSync(): void--><!--Device-WebCookieManager-static clearSessionCookieSync(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## configCookie

```TypeScript
static configCookie(url: string, value: string): Promise<void>
```

Set a single cookie (key-value pair) for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static configCookie(url: string, value: string): Promise<void>--><!--Device-WebCookieManager-static configCookie(url: string, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookie is to be set. |
| value | string | 是 | The cookie as a string, using the format of the 'Set-Cookie' HTTP response header. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A promise resolved after the cookies of given URL have been set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100005](../../apis-arkweb/errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified &lt;br&gt;in RFC 6265. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## configCookie

```TypeScript
static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>
```

Set a single cookie (key-value pair) for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>--><!--Device-WebCookieManager-static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookie is to be set. |
| value | string | 是 | The cookie as a string, using the format of the 'Set-Cookie' HTTP response header. |
| incognito | boolean | 是 | {@code true} set a single cookie (key-value pair) for the given URL in incognito mode; {@code false} otherwise. |
| includeHttpOnly | boolean | 是 | {@code true} HTTP-only cookies can also be overwritten; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A promise resolved after the cookies of given URL have been set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100005](../../apis-arkweb/errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified &lt;br&gt;in RFC 6265. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## configCookie

```TypeScript
static configCookie(url: string, value: string, callback: AsyncCallback<void>): void
```

Set a single cookie (key-value pair) for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static configCookie(url: string, value: string, callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static configCookie(url: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookie is to be set. |
| value | string | 是 | The cookie as a string, using the format of the 'Set-Cookie' HTTP response header. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Called after the cookies have been set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100005](../../apis-arkweb/errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified &lt;br&gt;in RFC 6265. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito?: boolean): void
```

Set a single cookie (key-value pair) for the given URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito?: boolean): void--><!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookie is to be set. |
| value | string | 是 | The cookie as a string, using the format of the 'Set-Cookie' HTTP response header. |
| incognito | boolean | 否 | {@code true} set a single cookie (key-value pair) for the given URL in incognito mode; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100005](../../apis-arkweb/errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified &lt;br&gt;in RFC 6265. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void
```

Set a single cookie (key-value pair) for the given URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void--><!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookie is to be set. |
| value | string | 是 | The cookie as a string, using the format of the 'Set-Cookie' HTTP response header. |
| incognito | boolean | 是 | {@code true} set a single cookie (key-value pair) for the given URL in incognito mode; {@code false} otherwise. |
| includeHttpOnly | boolean | 是 | {@code true} HTTP-only cookies can also be overwritten; {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100005](../../apis-arkweb/errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified &lt;br&gt;in RFC 6265. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## existCookie

```TypeScript
static existCookie(incognito?: boolean): boolean
```

Check whether exists any cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static existCookie(incognito?: boolean): boolean--><!--Device-WebCookieManager-static existCookie(incognito?: boolean): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | {@code true} check whether exists any cookies. in incognito mode; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if exists more than one cookie else false; |

## fetchAllCookies

```TypeScript
static fetchAllCookies(incognito: boolean): Promise<Array<WebHttpCookie>>
```

Fetches all stored cookies asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static fetchAllCookies(incognito: boolean): Promise<Array<WebHttpCookie>>--><!--Device-WebCookieManager-static fetchAllCookies(incognito: boolean): Promise<Array<WebHttpCookie>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 是 | {@code true} Gets all cookies in incognito context; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WebHttpCookie](arkts-na-webview-webhttpcookie-i.md)&gt;&gt; | A promise resolved after the cookies gotten. |

## fetchCookie

```TypeScript
static fetchCookie(url: string): Promise<string>
```

Gets all cookies for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static fetchCookie(url: string): Promise<string>--><!--Device-WebCookieManager-static fetchCookie(url: string): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookies are requested. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | A promise resolved after the cookies of given URL have been gotten. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## fetchCookie

```TypeScript
static fetchCookie(url: string, incognito: boolean): Promise<string>
```

Gets all cookies for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static fetchCookie(url: string, incognito: boolean): Promise<string>--><!--Device-WebCookieManager-static fetchCookie(url: string, incognito: boolean): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookies are requested. |
| incognito | boolean | 是 | {@code true} gets all cookies for the given URL in incognito mode; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | A promise resolved after the cookies of given URL have been gotten. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## fetchCookie

```TypeScript
static fetchCookie(url: string, callback: AsyncCallback<string>): void
```

Gets all cookies for the given URL Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static fetchCookie(url: string, callback: AsyncCallback<string>): void--><!--Device-WebCookieManager-static fetchCookie(url: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookies are requested. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | Called after the cookies of given URL have been gotten. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## fetchCookieSync

```TypeScript
static fetchCookieSync(url: string, incognito?: boolean): string
```

Gets all cookies for the given URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static fetchCookieSync(url: string, incognito?: boolean): string--><!--Device-WebCookieManager-static fetchCookieSync(url: string, incognito?: boolean): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | The URL for which the cookies are requested. |
| incognito | boolean | 否 | {@code true} gets all cookies for the given URL in incognito mode; {@code false} otherwise. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | The cookie value for the given URL. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

## isCookieAllowed

```TypeScript
static isCookieAllowed(): boolean
```

Get whether the instance can send and accept cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static isCookieAllowed(): boolean--><!--Device-WebCookieManager-static isCookieAllowed(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the instance can send and accept cookies else false. |

## isThirdPartyCookieAllowed

```TypeScript
static isThirdPartyCookieAllowed(): boolean
```

Get whether the instance can send and accept thirdparty cookies.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static isThirdPartyCookieAllowed(): boolean--><!--Device-WebCookieManager-static isThirdPartyCookieAllowed(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True if the instance can send and accept thirdparty cookies else false. |

## putAcceptCookieEnabled

```TypeScript
static putAcceptCookieEnabled(accept: boolean): void
```

Set whether the instance should send and accept cookies. By default this is set to be true.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static putAcceptCookieEnabled(accept: boolean): void--><!--Device-WebCookieManager-static putAcceptCookieEnabled(accept: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | Whether the instance should send and accept cookies. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## putAcceptThirdPartyCookieEnabled

```TypeScript
static putAcceptThirdPartyCookieEnabled(accept: boolean): void
```

Set whether the instance should send and accept thirdparty cookies. By default this is set to be false.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static putAcceptThirdPartyCookieEnabled(accept: boolean): void--><!--Device-WebCookieManager-static putAcceptThirdPartyCookieEnabled(accept: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | Whether the instance should send and accept thirdparty cookies. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieAsync

```TypeScript
static saveCookieAsync(): Promise<void>
```

Save the cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static saveCookieAsync(): Promise<void>--><!--Device-WebCookieManager-static saveCookieAsync(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A promise resolved after the cookies have been saved. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieAsync

```TypeScript
static saveCookieAsync(callback: AsyncCallback<void>): void
```

Save the cookies Asynchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static saveCookieAsync(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static saveCookieAsync(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Called after the cookies have been saved. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2. Incorrect parameter types. 3.Parameter verification failed. |

## saveCookieSync

```TypeScript
static saveCookieSync(): void
```

Save the cookies synchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static saveCookieSync(): void--><!--Device-WebCookieManager-static saveCookieSync(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setLazyInitializeWebEngine

```TypeScript
static setLazyInitializeWebEngine(lazy: boolean): void
```

Delays the initialization of the web engine. By default, the web engine is initialized when the CookieManager interface is called. By setting the 'lazy' parameter to true, the web engine will not be initialized when the CookieManager interface is called. Instead, the web engine will be initialized either when the web component is created or when initializeWebEngine is called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebCookieManager-static setLazyInitializeWebEngine(lazy: boolean): void--><!--Device-WebCookieManager-static setLazyInitializeWebEngine(lazy: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lazy | boolean | 是 | Controls whether to delay the initialization of the web engine. @static |

