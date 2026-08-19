# WebResourceResponse

WebResourceResponse是Web组件中表示HTTP响应并允许自定义网页资源响应的类。它在onHttpErrorReceive等事件中向应用提供服务器返回响应的状态码、状态描述、响应头、响应数据、编码、MIME类型等信息； 在资源请求拦截场景中允许应用自定义响应的状态码、状态描述、响应头、响应数据、编码、MIME类型及数据就绪状态，从而由应用接管特定资源的返回内容。示例代码参考 [onHttpErrorReceive事件](arkts-arkweb-web-attribute.md#onhttperrorreceive)。

**起始版本：** 8

<!--Device-unnamed-declare class WebResourceResponse--><!--Device-unnamed-declare class WebResourceResponse-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

WebResourceResponse的构造函数。用于创建HTTP响应对象，常用于资源请求拦截场景中自定义响应内容。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-constructor()--><!--Device-WebResourceResponse-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getReasonMessage

```TypeScript
getReasonMessage(): string
```

获取资源响应的状态码描述。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getReasonMessage(): string--><!--Device-WebResourceResponse-getReasonMessage(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的状态码描述，如'OK'、'Not Found'等。 |

## getResponseCode

```TypeScript
getResponseCode(): number
```

获取资源响应的状态码。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getResponseCode(): number--><!--Device-WebResourceResponse-getResponseCode(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回资源响应的状态码，如200表示成功，404表示未找到。 |

## getResponseData

```TypeScript
getResponseData(): string
```

获取资源响应数据。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getResponseData(): string--><!--Device-WebResourceResponse-getResponseData(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应数据，为HTML格式的字符串内容。 |

## getResponseDataEx

```TypeScript
getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined
```

获取资源响应数据，支持多种数据类型。与getResponseData相比，该方法支持返回number（文件句柄）、ArrayBuffer（二进制数据）、Resource（\$rawfile资源）等多种类型，建议在需要灵活数据类型支持 时优先使用。

**起始版本：** 13

<!--Device-WebResourceResponse-getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined--><!--Device-WebResourceResponse-getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | string返回HTML格式的字符串。 number返回文件句柄。 ArrayBuffer返回二进 制数据。 Resource返回`\\$rawfile`资源。 如果没有可用数据，返回`undefined`。 |

## getResponseEncoding

```TypeScript
getResponseEncoding(): string
```

获取资源响应的编码。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getResponseEncoding(): string--><!--Device-WebResourceResponse-getResponseEncoding(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的编码，如'utf-8'、'gbk'等字符集编码。 |

## getResponseHeader

```TypeScript
getResponseHeader(): Array<Header>
```

获取资源响应头。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getResponseHeader(): Array<Header>--><!--Device-WebResourceResponse-getResponseHeader(): Array<Header>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Header](arkts-arkweb-header-i.md)&gt; | 返回资源响应头。 |

## getResponseIsReady

```TypeScript
getResponseIsReady(): boolean
```

获取响应数据是否已准备就绪。

**起始版本：** 13

<!--Device-WebResourceResponse-getResponseIsReady(): boolean--><!--Device-WebResourceResponse-getResponseIsReady(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | `true`表示响应数据已准备好，`false`表示未准备好。 |

## getResponseMimeType

```TypeScript
getResponseMimeType(): string
```

获取资源响应的媒体（MIME）类型。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-getResponseMimeType(): string--><!--Device-WebResourceResponse-getResponseMimeType(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的媒体（MIME）类型，如'text/html'、'application/json'等。 |

## setReasonMessage

```TypeScript
setReasonMessage(reason: string): void
```

设置资源响应的状态码描述。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setReasonMessage(reason: string): void--><!--Device-WebResourceResponse-setReasonMessage(reason: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 要设置的资源响应的状态码描述。状态码描述是对状态码的文本说明，通常与状态码对应使用，例如状态码为200时描述可设为“OK”，状态码为404时描述可设为“Not Found”。该 描述会包含在HTTP响应中，便于客户端或开发者了解响应结果。 |

## setResponseCode

```TypeScript
setResponseCode(code: number): void
```

设置资源响应的状态码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseCode(code: number): void--><!--Device-WebResourceResponse-setResponseCode(code: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 要设置的资源响应的状态码。如果该资源请求失败或响应状态为错误状态，请参考 [@ohos.web.netErrorList](../../apis-na/arkts-apis/arkts-na-web-neterrorlist-webneterrorlist-e.md)设置相应错误码。常见错误码场景：404表示资源不存在，请检查资源路径；500表示服 务器内部错误，请检查服务器状态；403表示无访问权限，请申请相应访问权限；401表示未授权，请检查认证信息。根据错误码检查网络配置、服务器状态或资源访问权限。避免设置错误码为 ERR_IO_PENDING，设置为该错误码可 能会导致XMLHttpRequest同步请求阻塞。 |

## setResponseData

```TypeScript
setResponseData(data: string | number | Resource | ArrayBuffer): void
```

设置资源响应数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseData(data: string | number | Resource | ArrayBuffer): void--><!--Device-WebResourceResponse-setResponseData(data: string | number | Resource | ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| number \| Resource \| ArrayBuffer | 是 | 要设置的资源响应数据。string表示HTML格式的字符串。number表示文件句柄，此句柄由系统的Web组件负 责关闭。Resource表示应用rawfile目录下文件资源。ArrayBuffer表示资源的原始二进制数据。<br>**起始版本：** 11 |

## setResponseEncoding

```TypeScript
setResponseEncoding(encoding: string): void
```

设置资源响应的编码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseEncoding(encoding: string): void--><!--Device-WebResourceResponse-setResponseEncoding(encoding: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | 要设置的资源响应的编码。编码格式需要与响应数据的实际编码保持一致，编码格式会影响浏览器或客户端对响应内容的解析和展示。 |

## setResponseHeader

```TypeScript
setResponseHeader(header: Array<Header>): void
```

设置资源响应头。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseHeader(header: Array<Header>): void--><!--Device-WebResourceResponse-setResponseHeader(header: Array<Header>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| header | Array&lt;[Header](arkts-arkweb-header-i.md)&gt; | 是 | 要设置的资源响应头。响应头用于传递HTTP协议头信息，例如设置“Cache-Control”控制缓存策略，设置“Access-Control-Allow- Origin”实现跨域访问，设置“Content-Type”指定内容类型。设置响应头会影响浏览器或客户端对资源的处理方式。 |

## setResponseIsReady

```TypeScript
setResponseIsReady(IsReady: boolean): void
```

设置资源响应数据是否已经就绪。 > **说明：** > > - 在资源请求拦截场景中，应先调用setResponseData()、setResponseEncoding()、setResponseMimeType()、setResponseHeader()、 > setResponseCode()、setReasonMessage()等方法设置响应的各个属性。最后调用setResponseIsReady(true)来触发资源返回。 > > - 异步数据场景：需先调用setResponseIsReady(false)，待数据准备好后调用setResponseData()等设置方法，最后调用setResponseIsReady(true)来触发资源返回。 > > - 如果不正确设置调用顺序，可能导致XMLHttpRequest同步请求阻塞。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void--><!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| IsReady | boolean | 是 | 资源响应数据是否已经就绪。 <br>true表示资源响应数据已经就绪，false表示资源响应数据未就绪。 <br>如果数据是异步提供，需要显式设置为false。设置为非法值如null，undefined或者不设置都会被认为数据已经准备好。 |

## setResponseMimeType

```TypeScript
setResponseMimeType(mimeType: string): void
```

设置资源响应的媒体（MIME）类型。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseMimeType(mimeType: string): void--><!--Device-WebResourceResponse-setResponseMimeType(mimeType: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 要设置的资源响应的媒体（MIME）类型。常见的MIME类型包括：text/html（HTML文档）、application/json（JSON数据）、image/png（ PNG图片）等。 |

