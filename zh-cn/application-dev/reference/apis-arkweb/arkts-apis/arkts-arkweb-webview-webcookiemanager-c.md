# WebCookieManager

提供了用于管理网页Cookie的方法。

**起始版本：** 9

<!--Device-webview-class WebCookieManager--><!--Device-webview-class WebCookieManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="clearallcookies"></a>
## clearAllCookies

```TypeScript
static clearAllCookies(): Promise<void>
```

清除所有cookie。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearAllCookies(): Promise<void>--><!--Device-WebCookieManager-static clearAllCookies(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，用于获取清除所有cookie是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

<a id="clearallcookies-1"></a>
## clearAllCookies

```TypeScript
static clearAllCookies(callback: AsyncCallback<void>): void
```

异步callback方式清除所有cookie。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearAllCookies(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static clearAllCookies(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback回调，用于获取清除所有cookie是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

<a id="clearallcookiessync"></a>
## clearAllCookiesSync

```TypeScript
static clearAllCookiesSync(incognito?: boolean): void
```

清除所有cookie。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearAllCookiesSync(incognito?: boolean): void--><!--Device-WebCookieManager-static clearAllCookiesSync(incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | true表示清除隐私模式下Webview的所有内存cookies，false表示清除正常非隐私模式下的持久化cookies。 |

<a id="clearsessioncookie"></a>
## clearSessionCookie

```TypeScript
static clearSessionCookie(): Promise<void>
```

清除所有会话cookie。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearSessionCookie(): Promise<void>--><!--Device-WebCookieManager-static clearSessionCookie(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，用于获取清除所有会话cookie是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |

<a id="clearsessioncookie-1"></a>
## clearSessionCookie

```TypeScript
static clearSessionCookie(callback: AsyncCallback<void>): void
```

异步callback方式清除所有会话cookie。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearSessionCookie(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static clearSessionCookie(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback回调，用于获取清除所有会话cookie是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

<a id="clearsessioncookiesync"></a>
## clearSessionCookieSync

```TypeScript
static clearSessionCookieSync(): void
```

清除所有会话cookie。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static clearSessionCookieSync(): void--><!--Device-WebCookieManager-static clearSessionCookieSync(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="configcookie"></a>
## configCookie

```TypeScript
static configCookie(url: string, value: string): Promise<void>
```

指定url设置单个cookie的值。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static configCookie(url: string, value: string): Promise<void>--><!--Device-WebCookieManager-static configCookie(url: string, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url。 |
| value | string | 是 | 要设置的cookie的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，用于获取指定url设置单个cookie值是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="configcookie-1"></a>
## configCookie

```TypeScript
static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>
```

指定url设置单个cookie的值。使用Promise异步回调。

**起始版本：** 14

<!--Device-WebCookieManager-static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>--><!--Device-WebCookieManager-static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url。 |
| value | string | 是 | 要设置的cookie的值。 |
| incognito | boolean | 是 | true表示设置隐私模式下对应url的cookies，false表示设置正常非隐私模式下对应url的cookies。 |
| includeHttpOnly | boolean | 是 | true表示允许覆盖含有http-only的cookies，false表示不允许覆盖含有http-only的cookies。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，用于获取指定url设置单个cookie值是否成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="configcookie-2"></a>
## configCookie

```TypeScript
static configCookie(url: string, value: string, callback: AsyncCallback<void>): void
```

异步callback方式为指定url设置单个cookie的值。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static configCookie(url: string, value: string, callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static configCookie(url: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url。 |
| value | string | 是 | 要设置的cookie的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback回调，用于获取设置cookie的结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="configcookiesync"></a>
## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito?: boolean): void
```

为指定url设置单个cookie的值。

> **说明：**  
>  
> - configCookieSync中的url，可以指定域名的方式来使得页面内请求也附带上cookie。  
>  
> - 同步cookie的时机建议在Web组件加载之前完成。  
>  
> - cookie每30s周期性保存到磁盘中，也可以使用接口saveCookieAsync进行强制落盘。  
>  
> - value参数必须遵循Set-Cookie HTTP响应头的格式。形式为"key=value"的键值对，后面可跟随以分号分隔的cookie属性列表（例如"key=value;Max-Age=100"）。  
>  
> - 若存在相同host、path和名称的cookie，将被新cookie替换。若设置的cookie已过期，则不会存储该cookie。如需设置多个cookie，应多次调用此方法。  
>  
> - 若通过configCookieSync进行两次或多次设置cookie，则每次设置的cookie之间会通过"; "进行分隔。  
>  
> - 如果指定的值包含"Secure"属性，则url必须使用"https://"协议。  
>  
> - 如果要覆盖HttpOnly的cookies，需要在value中指定HttpOnly属性。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito?: boolean): void--><!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url，建议使用完整的url。 |
| value | string | 是 | 要设置的cookie的值。 |
| incognito | boolean | 否 | true表示设置隐私模式下对应url的cookies，false表示设置正常非隐私模式下对应url的cookies。<br>默认值：false。 <br>传入undefined或null会抛出异常错误码401。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="configcookiesync-1"></a>
## configCookieSync

```TypeScript
static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void
```

为指定url设置cookie的值。

> **说明：**  
>  
> - configCookieSync中的url，可以指定域名的方式来使得页面内请求也附带上cookie。  
>  
> - 同步cookie的时机建议在Web组件加载之前完成。  
>  
> - cookie每30s周期性保存到磁盘中，也可以使用接口saveCookieAsync进行强制落盘。  
>  
> - value参数必须遵循Set-Cookie HTTP响应头的格式。形式为"key=value"的键值对，后面可跟随以分号分隔的cookie属性列表（例如"key=value;Max-Age=100"）。  
>  
> - 若存在相同host、path和名称的cookie，将被新cookie替换。若设置的cookie已过期，则不会存储该cookie。如需设置多个cookie，应多次调用此方法。  
>  
> - 若通过configCookieSync进行两次或多次设置cookie，则每次设置的cookie之间会通过"; "进行分隔。  
>  
> - 如果指定的值包含"Secure"属性，则url必须使用"https://"协议。

**起始版本：** 14

<!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void--><!--Device-WebCookieManager-static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url。 |
| value | string | 是 | 要设置的cookie的值。 |
| incognito | boolean | 是 | true表示设置隐私模式下对应url的cookies，false表示设置正常非隐私模式下对应url的cookies。 |
| includeHttpOnly | boolean | 是 | true表示允许覆盖含有http-only的cookies，false表示不允许覆盖含有http-only的cookies。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="deleteentirecookie"></a>
## deleteEntireCookie

```TypeScript
static deleteEntireCookie(): void
```

清除所有cookie。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** clearAllCookiesSync

<!--Device-WebCookieManager-static deleteEntireCookie(): void--><!--Device-WebCookieManager-static deleteEntireCookie(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="deletesessioncookie"></a>
## deleteSessionCookie

```TypeScript
static deleteSessionCookie(): void
```

清除所有会话cookie。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** clearSessionCookieSync

<!--Device-WebCookieManager-static deleteSessionCookie(): void--><!--Device-WebCookieManager-static deleteSessionCookie(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="existcookie"></a>
## existCookie

```TypeScript
static existCookie(incognito?: boolean): boolean
```

获取是否存在cookie。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static existCookie(incognito?: boolean): boolean--><!--Device-WebCookieManager-static existCookie(incognito?: boolean): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 否 | true表示隐私模式下查询是否存在cookies，false表示正常非隐私模式下查询是否存在cookies。<br>默认值：false。<br>传入undefined或null时返回undefined。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示存在cookie，false表示不存在cookie。 |

<a id="fetchallcookies"></a>
## fetchAllCookies

```TypeScript
static fetchAllCookies(incognito: boolean):  Promise<Array<WebHttpCookie>>
```

异步获取所有cookie。

**起始版本：** 23

<!--Device-WebCookieManager-static fetchAllCookies(incognito: boolean):  Promise<Array<WebHttpCookie>>--><!--Device-WebCookieManager-static fetchAllCookies(incognito: boolean):  Promise<Array<WebHttpCookie>>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| incognito | boolean | 是 | {@code true} 隐私模式下获取所有Cookie。 {@code false} 非隐私模式下获取所有Cookie。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WebHttpCookie&gt;&gt; | - Promise对象，用于获取所有cookie及其对应的字段值。 |

<a id="fetchcookie"></a>
## fetchCookie

```TypeScript
static fetchCookie(url: string): Promise<string>
```

以Promise方式异步获取指定url对应cookie的值。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static fetchCookie(url: string): Promise<string>--><!--Device-WebCookieManager-static fetchCookie(url: string): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要获取的cookie所属的url。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise实例，用于获取指定url对应的cookie值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

<a id="fetchcookie-1"></a>
## fetchCookie

```TypeScript
static fetchCookie(url: string, incognito: boolean): Promise<string>
```

以Promise方式异步获取指定url对应cookie的值。

**起始版本：** 14

<!--Device-WebCookieManager-static fetchCookie(url: string, incognito: boolean): Promise<string>--><!--Device-WebCookieManager-static fetchCookie(url: string, incognito: boolean): Promise<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要获取的cookie所属的url。 |
| incognito | boolean | 是 | true表示获取隐私模式下webview的内存cookies，false表示正常非隐私模式下的cookies。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise实例，用于获取指定url对应的cookie值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

<a id="fetchcookie-2"></a>
## fetchCookie

```TypeScript
static fetchCookie(url: string, callback: AsyncCallback<string>): void
```

异步callback方式获取指定url对应cookie的值。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static fetchCookie(url: string, callback: AsyncCallback<string>): void--><!--Device-WebCookieManager-static fetchCookie(url: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要获取的cookie所属的url。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 在获取到指定URL的Cookie之后调用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

<a id="fetchcookiesync"></a>
## fetchCookieSync

```TypeScript
static fetchCookieSync(url: string, incognito?: boolean): string
```

获取指定url对应cookie的值。

> **说明：**  
>  
> - 系统会自动清理过期的cookie，对于同名key的数据，新数据将会覆盖前一个数据。  
>  
> - 为了获取可正常使用的cookie值，fetchCookieSync需传入完整链接。  
>  
> - fetchCookieSync用于获取所有的cookie值，每条cookie值之间会通过"; "进行分隔，但无法单独获取某一条特定的cookie值。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static fetchCookieSync(url: string, incognito?: boolean): string--><!--Device-WebCookieManager-static fetchCookieSync(url: string, incognito?: boolean): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要获取的cookie所属的url。 |
| incognito | boolean | 否 | true表示获取隐私模式下webview的内存cookies，false表示正常非隐私模式下的cookies。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 指定url对应的cookie的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

<a id="getcookie"></a>
## getCookie

```TypeScript
static getCookie(url: string): string
```

获取指定url对应cookie的值。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** fetchCookieSync

<!--Device-WebCookieManager-static getCookie(url: string): string--><!--Device-WebCookieManager-static getCookie(url: string): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要获取的cookie所属的url。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - 指定url对应的cookie的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |

<a id="iscookieallowed"></a>
## isCookieAllowed

```TypeScript
static isCookieAllowed(): boolean
```

获取WebCookieManager实例是否拥有发送和接收cookie的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static isCookieAllowed(): boolean--><!--Device-WebCookieManager-static isCookieAllowed(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否拥有发送和接收cookie的权限。<br>true表示拥有发送和接收cookie的权限，false表示无发送和接收cookie的权限。<br>默认值：true。 |

<a id="isthirdpartycookieallowed"></a>
## isThirdPartyCookieAllowed

```TypeScript
static isThirdPartyCookieAllowed(): boolean
```

获取WebCookieManager实例是否拥有发送和接收第三方cookie的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static isThirdPartyCookieAllowed(): boolean--><!--Device-WebCookieManager-static isThirdPartyCookieAllowed(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否拥有发送和接收第三方cookie的权限。<br>true表示拥有发送和接收第三方cookie的权限，false表示无发送和接收第三方cookie的权限。<br>默认值：false。 |

<a id="putacceptcookieenabled"></a>
## putAcceptCookieEnabled

```TypeScript
static putAcceptCookieEnabled(accept: boolean): void
```

设置WebCookieManager实例是否拥有发送和接收cookie的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static putAcceptCookieEnabled(accept: boolean): void--><!--Device-WebCookieManager-static putAcceptCookieEnabled(accept: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | 设置是否拥有发送和接收cookie的权限，默认为true，表示拥有发送和接收cookie的权限。false表示没有发送和接收cookie的权限。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

<a id="putacceptthirdpartycookieenabled"></a>
## putAcceptThirdPartyCookieEnabled

```TypeScript
static putAcceptThirdPartyCookieEnabled(accept: boolean): void
```

设置WebCookieManager实例是否拥有发送和接收第三方cookie的权限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static putAcceptThirdPartyCookieEnabled(accept: boolean): void--><!--Device-WebCookieManager-static putAcceptThirdPartyCookieEnabled(accept: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accept | boolean | 是 | 是否允许设置、获取第三方cookie。<br>true表示允许设置、获取第三方cookie，false表示不允许设置、获取第三方cookie。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

<a id="savecookieasync"></a>
## saveCookieAsync

```TypeScript
static saveCookieAsync(): Promise<void>
```

将当前可通过fetchCookie获取到的所有需要持久化的cookie以Promise方法异步保存到磁盘中。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static saveCookieAsync(): Promise<void>--><!--Device-WebCookieManager-static saveCookieAsync(): Promise<void>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | - Promise实例，用于获取cookie是否成功保存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

<a id="savecookieasync-1"></a>
## saveCookieAsync

```TypeScript
static saveCookieAsync(callback: AsyncCallback<void>): void
```

将当前可通过fetchCookie获取到的所有需要持久化的cookie异步保存到磁盘中。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebCookieManager-static saveCookieAsync(callback: AsyncCallback<void>): void--><!--Device-WebCookieManager-static saveCookieAsync(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback回调，用于获取cookie是否成功保存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |

<a id="savecookiesync"></a>
## saveCookieSync

```TypeScript
static saveCookieSync(): void
```

将当前可通过fetchCookie获取到的所有需要持久化的cookie同步保存到磁盘中。

> **说明：**  
>  
> - saveCookieSync用于强制将需要持久化的cookies写入磁盘。PC/2in1和Tablet设备不会持久化session cookie，即使调用saveCookieSync，也不会将session  
> cookie写入磁盘。  
>  
> - saveCookieSync将阻塞调用者直到操作完成，期间可能会执行I/O操作。

**起始版本：** 15

<!--Device-WebCookieManager-static saveCookieSync(): void--><!--Device-WebCookieManager-static saveCookieSync(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="setcookie"></a>
## setCookie

```TypeScript
static setCookie(url: string, value: string): void
```

为指定url设置单个cookie的值。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** configCookieSync

<!--Device-WebCookieManager-static setCookie(url: string, value: string): void--><!--Device-WebCookieManager-static setCookie(url: string, value: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要设置的cookie所属的url。 |
| value | string | 是 | 要设置的cookie的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100002](../errorcode-webview.md#17100002-url格式错误) | URL error. No valid cookie found for the specified URL. |
| [17100005](../errorcode-webview.md#17100005-cookie-value格式错误) | The provided cookie value is invalid. It must follow the format specified<br>in RFC 6265. |

<a id="setlazyinitializewebengine"></a>
## setLazyInitializeWebEngine

```TypeScript
static setLazyInitializeWebEngine(lazy: boolean): void
```

Delays the initialization of the web engine. By default, the web engine is initialized when the CookieManager interface is called. By setting the 'lazy' parameter to true, the web engine will not be initialized when the CookieManager interface is called. Instead, the web engine will be initialized either when the web component is created or when initializeWebEngine is called.

**起始版本：** 22

<!--Device-WebCookieManager-static setLazyInitializeWebEngine(lazy: boolean): void--><!--Device-WebCookieManager-static setLazyInitializeWebEngine(lazy: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lazy | boolean | 是 | Controls whether to delay the initialization of the web engine. |

