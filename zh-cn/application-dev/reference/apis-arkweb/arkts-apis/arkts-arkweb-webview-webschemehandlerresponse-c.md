# WebSchemeHandlerResponse

请求的响应，可以为被拦截的请求创建一个Response并填充自定义的内容返回给Web组件。

**起始版本：** 12

<!--Device-webview-class WebSchemeHandlerResponse--><!--Device-webview-class WebSchemeHandlerResponse-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-constructor()--><!--Device-WebSchemeHandlerResponse-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="getencoding"></a>
## getEncoding

```TypeScript
getEncoding(): string
```

获取Response的字符集。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getEncoding(): string--><!--Device-WebSchemeHandlerResponse-getEncoding(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 字符集。 |

<a id="getheaderbyname"></a>
## getHeaderByName

```TypeScript
getHeaderByName(name: string): string
```

按名称获取Response头部字段值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getHeaderByName(name: string): string--><!--Device-WebSchemeHandlerResponse-getHeaderByName(name: string): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 头部（header）的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 头部（header）的值。 |

<a id="getmimetype"></a>
## getMimeType

```TypeScript
getMimeType(): string
```

获取Response的媒体类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getMimeType(): string--><!--Device-WebSchemeHandlerResponse-getMimeType(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 媒体类型。 |

<a id="getneterrorcode"></a>
## getNetErrorCode

```TypeScript
getNetErrorCode(): WebNetErrorList
```

获取Response的网络错误码。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getNetErrorCode(): WebNetErrorList--><!--Device-WebSchemeHandlerResponse-getNetErrorCode(): WebNetErrorList-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | 获取Response的网络错误码。 |

<a id="getstatus"></a>
## getStatus

```TypeScript
getStatus(): number
```

获取Response的Http状态码。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getStatus(): number--><!--Device-WebSchemeHandlerResponse-getStatus(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取Response的Http状态码。 |

<a id="getstatustext"></a>
## getStatusText

```TypeScript
getStatusText(): string
```

获取Response的状态文本。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getStatusText(): string--><!--Device-WebSchemeHandlerResponse-getStatusText(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 状态文本。 |

<a id="geturl"></a>
## getUrl

```TypeScript
getUrl(): string
```

获取重定向或由于HSTS而更改后的URL。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-getUrl(): string--><!--Device-WebSchemeHandlerResponse-getUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取经过重定向或由于HSTS而更改后的URL。 |

<a id="setencoding"></a>
## setEncoding

```TypeScript
setEncoding(encoding: string): void
```

给当前的Response设置字符集。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setEncoding(encoding: string): void--><!--Device-WebSchemeHandlerResponse-setEncoding(encoding: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | 字符集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

<a id="setheaderbyname"></a>
## setHeaderByName

```TypeScript
setHeaderByName(name: string, value: string, overwrite: boolean): void
```

给当前的Response设置头信息。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setHeaderByName(name: string, value: string, overwrite: boolean): void--><!--Device-WebSchemeHandlerResponse-setHeaderByName(name: string, value: string, overwrite: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 头部（header）的名称。 |
| value | string | 是 | 头部（header）的值。 |
| overwrite | boolean | 是 | 如果为true，将覆盖现有的头部，否则不覆盖。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

<a id="setmimetype"></a>
## setMimeType

```TypeScript
setMimeType(type: string): void
```

给当前的Response设置媒体类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setMimeType(type: string): void--><!--Device-WebSchemeHandlerResponse-setMimeType(type: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 媒体类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

<a id="setneterrorcode"></a>
## setNetErrorCode

```TypeScript
setNetErrorCode(code: WebNetErrorList): void
```

给当前的Response设置网络错误码。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setNetErrorCode(code: WebNetErrorList): void--><!--Device-WebSchemeHandlerResponse-setNetErrorCode(code: WebNetErrorList): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | 是 | 网络错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

<a id="setstatus"></a>
## setStatus

```TypeScript
setStatus(code: number): void
```

给当前的Response设置HTTP状态码。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setStatus(code: number): void--><!--Device-WebSchemeHandlerResponse-setStatus(code: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Http状态码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

<a id="setstatustext"></a>
## setStatusText

```TypeScript
setStatusText(text: string): void
```

给当前的Response设置状态文本。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setStatusText(text: string): void--><!--Device-WebSchemeHandlerResponse-setStatusText(text: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 状态文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

<a id="seturl"></a>
## setUrl

```TypeScript
setUrl(url: string): void
```

给当前的Response设置重定向或因HSTS而更改后的URL，设置了url后会触发请求的跳转。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandlerResponse-setUrl(url: string): void--><!--Device-WebSchemeHandlerResponse-setUrl(url: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 即将要跳转的URL。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

