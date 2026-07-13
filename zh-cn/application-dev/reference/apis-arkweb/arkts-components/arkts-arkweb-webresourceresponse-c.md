# WebResourceResponse

Web组件资源响应对象。

**起始版本：** 8

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## getReasonMessage

```TypeScript
getReasonMessage(): string
```

获取资源响应的状态码描述。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的状态码描述。 |

## getResponseCode

```TypeScript
getResponseCode(): number
```

获取资源响应的状态码。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回资源响应的状态码。 |

## getResponseData

```TypeScript
getResponseData(): string
```

获取资源响应数据。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应数据。 |

## getResponseDataEx

```TypeScript
getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined
```

获取资源响应数据，支持多种数据类型。

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response data.string type indicate string in HTML format.number type indicate file handle.Resource type indicate $rawfile resource.ArrayBuffer type indicate binary data. |

## getResponseEncoding

```TypeScript
getResponseEncoding(): string
```

获取资源响应的编码。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的编码。 |

## getResponseHeader

```TypeScript
getResponseHeader(): Array<Header>
```

获取资源响应头。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Header&gt; | 返回资源响应头。 |

## getResponseIsReady

```TypeScript
getResponseIsReady(): boolean
```

获取响应数据是否已准备就绪。

**起始版本：** 13

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

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回资源响应的媒体（MIME）类型。 |

## setReasonMessage

```TypeScript
setReasonMessage(reason: string): void
```

设置资源响应的状态码描述。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 要设置的资源响应的状态码描述。 |

## setResponseCode

```TypeScript
setResponseCode(code: number): void
```

设置资源响应的状态码。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 要设置的资源响应的状态码。 |

## setResponseData

```TypeScript
setResponseData(data: string | number | Resource | ArrayBuffer): void
```

设置资源响应数据。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| number \| Resource \| ArrayBuffer | 是 | 要设置的资源响应数据。string表示HTML格式的字符串。number表示文件句柄，此句柄由系统的Web组件负责关闭。Resource表示应用rawfile目录下文件资源.<br>**起始版本：** 9 - 10 |

## setResponseEncoding

```TypeScript
setResponseEncoding(encoding: string): void
```

设置资源响应的编码。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | 要设置的资源响应的编码。 |

## setResponseHeader

```TypeScript
setResponseHeader(header: Array<Header>): void
```

设置资源响应头。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| header | Array&lt;Header&gt; | 是 | 要设置的资源响应头。 |

## setResponseIsReady

```TypeScript
setResponseIsReady(IsReady: boolean): void
```

设置资源响应数据是否已经就绪。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| IsReady | boolean | 是 | 资源响应数据是否已经就绪。 |

## setResponseMimeType

```TypeScript
setResponseMimeType(mimeType: string): void
```

设置资源响应的媒体（MIME）类型。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 要设置的资源响应的媒体（MIME）类型。 |

