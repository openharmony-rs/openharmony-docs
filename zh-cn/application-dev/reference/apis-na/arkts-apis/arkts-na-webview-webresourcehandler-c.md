# WebResourceHandler

Used to intercept url requests. Response headers and body can be sent through WebResourceHandler.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-webview-class WebResourceHandler--><!--Device-webview-class WebResourceHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## didFail

```TypeScript
didFail(code: WebNetErrorList): void
```

Notify that this request should be failed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebResourceHandler-didFail(code: WebNetErrorList): void--><!--Device-WebResourceHandler-didFail(code: WebNetErrorList): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [WebNetErrorList](../../apis-arkweb/arkts-apis/arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | 是 | Set response error code to intercept. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100021](../../apis-arkweb/errorcode-webview.md#17100021-webresourcehandler已经失效) | The resource handler is invalid. |

## didFail

```TypeScript
didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void
```

Notify that this request should be failed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebResourceHandler-didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void--><!--Device-WebResourceHandler-didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | [WebNetErrorList](../../apis-arkweb/arkts-apis/arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | 是 | Set response error code to intercept. |
| completeIfNoResponse | boolean | 是 | If completeIfNoResponse is true, when DidFailWithError is called, if DidReceiveResponse has not been called, a response is automatically constructed and the current request is terminated. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100101](../../apis-arkweb/errorcode-webview.md#17100101-使用了错误的网络错误码) | The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList. |
| [17100021](../../apis-arkweb/errorcode-webview.md#17100021-webresourcehandler已经失效) | The resource handler is invalid. |

## didFinish

```TypeScript
didFinish(): void
```

Notify that this request should be finished and there is no more data available.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebResourceHandler-didFinish(): void--><!--Device-WebResourceHandler-didFinish(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100021](../../apis-arkweb/errorcode-webview.md#17100021-webresourcehandler已经失效) | The resource handler is invalid. |

## didReceiveResponse

```TypeScript
didReceiveResponse(response: WebSchemeHandlerResponse): void
```

Pass response headers to intercepted requests.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebResourceHandler-didReceiveResponse(response: WebSchemeHandlerResponse): void--><!--Device-WebResourceHandler-didReceiveResponse(response: WebSchemeHandlerResponse): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | [WebSchemeHandlerResponse](arkts-na-webview-webschemehandlerresponse-c.md) | 是 | Set response header to intercept. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../../apis-arkweb/errorcode-webview.md#17100021-webresourcehandler已经失效) | The resource handler is invalid. |

## didReceiveResponseBody

```TypeScript
didReceiveResponseBody(data: ArrayBuffer): void
```

Pass response body data to intercepted requests.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebResourceHandler-didReceiveResponseBody(data: ArrayBuffer): void--><!--Device-WebResourceHandler-didReceiveResponseBody(data: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | Set response body to intercept. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../../apis-arkweb/errorcode-webview.md#17100021-webresourcehandler已经失效) | The resource handler is invalid. |

