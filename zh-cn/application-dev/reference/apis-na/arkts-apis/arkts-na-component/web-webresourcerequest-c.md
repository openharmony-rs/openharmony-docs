# WebResourceRequest

Defines the Web resource request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WebResourceRequest--><!--Device-unnamed-export declare class WebResourceRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-constructor()--><!--Device-WebResourceRequest-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getRequestHeader

```TypeScript
getRequestHeader(): Array<Header>
```

Gets request headers.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-getRequestHeader(): Array<Header>--><!--Device-WebResourceRequest-getRequestHeader(): Array<Header>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | Return the request headers |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

Get request method.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-getRequestMethod(): string--><!--Device-WebResourceRequest-getRequestMethod(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the request method. |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

Gets the request URL.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-getRequestUrl(): string--><!--Device-WebResourceRequest-getRequestUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return the request URL. |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

Check whether the request is for getting the main frame.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-isMainFrame(): boolean--><!--Device-WebResourceRequest-isMainFrame(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return { |

## isRedirect

```TypeScript
isRedirect(): boolean
```

Check whether the request redirects.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-isRedirect(): boolean--><!--Device-WebResourceRequest-isRedirect(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return { |

## isRequestGesture

```TypeScript
isRequestGesture(): boolean
```

Check whether the request is associated with gesture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceRequest-isRequestGesture(): boolean--><!--Device-WebResourceRequest-isRequestGesture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Return { |

