# WebResourceResponse

Defines the Web resource response.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WebResourceResponse--><!--Device-unnamed-export declare class WebResourceResponse-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-constructor()--><!--Device-WebResourceResponse-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getReasonMessage

```TypeScript
getReasonMessage(): string
```

Gets the reason message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getReasonMessage(): string--><!--Device-WebResourceResponse-getReasonMessage(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the reason message. |

## getResponseCode

```TypeScript
getResponseCode(): int
```

Gets the response code.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseCode(): int--><!--Device-WebResourceResponse-getResponseCode(): int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return the response code. |

## getResponseData

```TypeScript
getResponseData(): string
```

Gets the response data.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseData(): string--><!--Device-WebResourceResponse-getResponseData(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response data. |

## getResponseDataEx

```TypeScript
getResponseDataEx(): string | int | ArrayBuffer | Resource | undefined
```

Gets the response data.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseDataEx(): string | int | ArrayBuffer | Resource | undefined--><!--Device-WebResourceResponse-getResponseDataEx(): string | int | ArrayBuffer | Resource | undefined-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response data. string type indicate string in HTML format. number type indicate file handle. Resource type indicate \\$rawfile resource. ArrayBuffer type indicate binary data. |

## getResponseEncoding

```TypeScript
getResponseEncoding(): string
```

Gets the response encoding.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseEncoding(): string--><!--Device-WebResourceResponse-getResponseEncoding(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response encoding. |

## getResponseHeader

```TypeScript
getResponseHeader(): Array<Header>
```

Gets the response headers.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseHeader(): Array<Header>--><!--Device-WebResourceResponse-getResponseHeader(): Array<Header>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Header](arkts-na-web-header-i.md)&gt; | Return the response headers. |

## getResponseIsReady

```TypeScript
getResponseIsReady(): boolean
```

Gets whether the response is ready.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseIsReady(): boolean--><!--Device-WebResourceResponse-getResponseIsReady(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | True indicates the response data is ready and false is not ready. |

## getResponseMimeType

```TypeScript
getResponseMimeType(): string
```

Gets the response MIME type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-getResponseMimeType(): string--><!--Device-WebResourceResponse-getResponseMimeType(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the response MIME type. |

## setReasonMessage

```TypeScript
setReasonMessage(reason: string): void
```

Sets the reason message.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setReasonMessage(reason: string): void--><!--Device-WebResourceResponse-setReasonMessage(reason: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | the reason message. |

## setResponseCode

```TypeScript
setResponseCode(code: int): void
```

Sets the response code.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseCode(code: int): void--><!--Device-WebResourceResponse-setResponseCode(code: int): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | int | 是 | the response code. |

## setResponseData

```TypeScript
setResponseData(data: string | int | Resource | ArrayBuffer): void
```

Sets the response data.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseData(data: string | int | Resource | ArrayBuffer): void--><!--Device-WebResourceResponse-setResponseData(data: string | int | Resource | ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| int \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| ArrayBuffer | 是 | the response data. string type indicate strings in HTML format. number type indicate file handle. Resource type indicate \\$rawfile resource. ArrayBuffer type indicate binary data. |

## setResponseEncoding

```TypeScript
setResponseEncoding(encoding: string): void
```

Sets the response encoding.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseEncoding(encoding: string): void--><!--Device-WebResourceResponse-setResponseEncoding(encoding: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 是 | the response encoding. |

## setResponseHeader

```TypeScript
setResponseHeader(header: Array<Header>): void
```

Sets the response headers.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseHeader(header: Array<Header>): void--><!--Device-WebResourceResponse-setResponseHeader(header: Array<Header>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| header | Array&lt;[Header](arkts-na-web-header-i.md)&gt; | 是 | the response headers. |

## setResponseIsReady

```TypeScript
setResponseIsReady(IsReady: boolean): void
```

Sets the response is ready or not.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void--><!--Device-WebResourceResponse-setResponseIsReady(IsReady: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| IsReady | boolean | 是 | whether the response is ready. |

## setResponseMimeType

```TypeScript
setResponseMimeType(mimeType: string): void
```

Sets the response MIME type.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebResourceResponse-setResponseMimeType(mimeType: string): void--><!--Device-WebResourceResponse-setResponseMimeType(mimeType: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | the response MIME type. |

