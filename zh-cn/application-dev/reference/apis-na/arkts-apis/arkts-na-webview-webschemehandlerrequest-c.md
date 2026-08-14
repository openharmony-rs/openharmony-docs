# WebSchemeHandlerRequest

Defines the Web resource request used for scheme handler.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebSchemeHandlerRequest--><!--Device-webview-class WebSchemeHandlerRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getFrameUrl

```TypeScript
getFrameUrl(): string
```

Gets the URL of frame which trigger this request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getFrameUrl(): string--><!--Device-WebSchemeHandlerRequest-getFrameUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the URL of frame which trigger this request. |

## getHeader

```TypeScript
getHeader(): Array<WebHeader>
```

Gets request headers.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getHeader(): Array<WebHeader>--><!--Device-WebSchemeHandlerRequest-getHeader(): Array<WebHeader>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WebHeader&gt; | Return the request headers. |

## getHttpBodyStream

```TypeScript
getHttpBodyStream(): WebHttpBodyStream | null
```

Get http body stream.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getHttpBodyStream(): WebHttpBodyStream | null--><!--Device-WebSchemeHandlerRequest-getHttpBodyStream(): WebHttpBodyStream | null-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebHttpBodyStream](arkts-na-webview-webhttpbodystream-c.md) | Return http body stream. If request has no http body stream, return null. |

## getReferrer

```TypeScript
getReferrer(): string
```

Get referrer of request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getReferrer(): string--><!--Device-WebSchemeHandlerRequest-getReferrer(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return referrer of request. |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

Get request method.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getRequestMethod(): string--><!--Device-WebSchemeHandlerRequest-getRequestMethod(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the request method. |

## getRequestResourceType

```TypeScript
getRequestResourceType(): WebResourceType
```

Get request's resource type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getRequestResourceType(): WebResourceType--><!--Device-WebSchemeHandlerRequest-getRequestResourceType(): WebResourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebResourceType](arkts-na-webview-webresourcetype-e.md) | Return the request's resource type. |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

Gets the request URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-getRequestUrl(): string--><!--Device-WebSchemeHandlerRequest-getRequestUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the request URL. |

## hasGesture

```TypeScript
hasGesture(): boolean
```

Check whether the request is associated with gesture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-hasGesture(): boolean--><!--Device-WebSchemeHandlerRequest-hasGesture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether request has user gesture. |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

Check whether the request is for getting the main frame.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebSchemeHandlerRequest-isMainFrame(): boolean--><!--Device-WebSchemeHandlerRequest-isMainFrame(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether request is main frame. |

