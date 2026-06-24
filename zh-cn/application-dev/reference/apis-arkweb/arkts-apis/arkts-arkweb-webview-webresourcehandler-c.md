# WebResourceHandler

Used to intercept url requests. Response headers and body can be sent through
WebResourceHandler.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## didFail

```TypeScript
didFail(code: WebNetErrorList): void
```

通知ArkWeb内核被拦截请求应该返回失败。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | WebNetErrorList | 是 | 网络错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

## didFail

```TypeScript
didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void
```

Notify that this request should be failed.

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | WebNetErrorList | 是 | Set response error code to intercept. |
| completeIfNoResponse | boolean | 是 | If completeIfNoResponse is true, when DidFailWithError is called, if<br/>DidReceiveResponse has not been called, a response is automatically<br/>constructed and the current request is terminated. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100101](../../errorcode-universal.md#17100101-The) | The errorCode is either ARKWEB_NET_OK or outside the range of error codes<br/>in WebNetErrorList. |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

## didFail

```TypeScript
didFail(code: WebNetErrorList, completeIfNoResponse: boolean, customErrorCode: number): void
```

Notify that this request should be failed.

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | WebNetErrorList | 是 | Set response error code to intercept. |
| completeIfNoResponse | boolean | 是 | If completeIfNoResponse is true, when DidFailWithError is called,<br/>if DidReceiveResponse has not been called, a response is automatically constructed and the current<br/>request is terminated. |
| customErrorCode | number | 是 | The custom error code for this response, Web engine will pass the custom<br/>error code directly to the application through onErrorReceive. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

## didFinish

```TypeScript
didFinish(): void
```

通知Web组件被拦截的请求已经完成，并且没有更多的数据可用。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

## didReceiveResponse

```TypeScript
didReceiveResponse(response: WebSchemeHandlerResponse): void
```

将构造的响应头传递给被拦截的请求。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | WebSchemeHandlerResponse | 是 | 该拦截请求的响应。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

## didReceiveResponseBody

```TypeScript
didReceiveResponseBody(data: ArrayBuffer): void
```

将构造的响应体传递给被拦截的请求。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | 响应体数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../../errorcode-universal.md#17100021-The) | The resource handler is invalid. |

