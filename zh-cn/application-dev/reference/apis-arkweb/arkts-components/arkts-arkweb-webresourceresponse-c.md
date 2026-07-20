# WebResourceResponse

Web组件资源响应对象。

**起始版本：** 8

<!--Device-unnamed-declare class WebResourceResponse--><!--Device-unnamed-declare class WebResourceResponse-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-constructor()--><!--Device-WebResourceResponse-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="getreasonmessage"></a>
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
| string | 返回资源响应的状态码描述。 |

<a id="getresponsecode"></a>
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
| number | 返回资源响应的状态码。 |

<a id="getresponsedata"></a>
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
| string | 返回资源响应数据。 |

<a id="getresponsedataex"></a>
## getResponseDataEx

```TypeScript
getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined
```

获取资源响应数据，支持多种数据类型。

**起始版本：** 13

<!--Device-WebResourceResponse-getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined--><!--Device-WebResourceResponse-getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response data.string type indicate string in HTML format.number type indicate file handle.Resource type indicate $rawfile resource.ArrayBuffer type indicate binary data. |

<a id="getresponseencoding"></a>
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
| string | 返回资源响应的编码。 |

<a id="getresponseheader"></a>
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
| Array&lt;Header&gt; | 返回资源响应头。 |

<a id="getresponseisready"></a>
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

<a id="getresponsemimetype"></a>
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
| string | 返回资源响应的媒体（MIME）类型。 |

<a id="setreasonmessage"></a>
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
| reason | string | 是 | 要设置的资源响应的状态码描述。 |

<a id="setresponsecode"></a>
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
| code | number | 是 | 要设置的资源响应的状态码。 |

<a id="setresponsedata"></a>
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
| data | string \| number \| Resource \| ArrayBuffer | 是 | 要设置的资源响应数据。string表示HTML格式的字符串。number表示文件句柄，此句柄由系统的Web组件负责关闭。Resource表示应用rawfile目录下文件资源.<br>**起始版本：** 9 - 10 |

<a id="setresponseencoding"></a>
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
| encoding | string | 是 | 要设置的资源响应的编码。 |

<a id="setresponseheader"></a>
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
| header | Array&lt;Header&gt; | 是 | 要设置的资源响应头。 |

<a id="setresponseisready"></a>
## setResponseIsReady

```TypeScript
setResponseIsReady(IsReady: boolean): void
```

设置资源响应数据是否已经就绪。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void--><!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| IsReady | boolean | 是 | 资源响应数据是否已经就绪。 |

<a id="setresponsemimetype"></a>
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
| mimeType | string | 是 | 要设置的资源响应的媒体（MIME）类型。 |

