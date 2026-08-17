# WebSchemeHandler

WebSchemeHandler是用于拦截指定scheme（协议）的网络请求的拦截器类，支持自定义协议处理、本地资源替换、特定请求拦截等场景。开发者通过实现onRequestStart回调来决定是否拦截某个请求，被拦截的请求可通过 WebResourceHandler自定义响应内容。通过WebviewController的 [setWebSchemeHandler](arkts-arkweb-webview-webviewcontroller-c.md#setwebschemehandler)方法将WebSchemeHandler实例注册到指定的scheme上，从而实现对该 scheme所有请求的截获和处理。 WebSchemeHandler与[WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md#webschemehandlerrequest)、 [WebResourceHandler](arkts-arkweb-webview-webresourcehandler-c.md#webresourcehandler)、 [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md#webschemehandlerresponse)配合使用：onRequestStart回调接收WebSchemeHandlerRequest（被拦 截的请求信息）和WebResourceHandler（用于返回自定义响应的处理器），返回boolean值表示是否拦截。onRequestStop在请求结束时触发（仅对已拦截的请求），用于资源清理。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

<!--Device-webview-class WebSchemeHandler--><!--Device-webview-class WebSchemeHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onRequestStart

```TypeScript
onRequestStart(
      callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void
```

当请求开始时的回调，在该回调函数中可以决定是否拦截该请求。当回调返回false时，表示不拦截此请求，此时handler失效；当回调返回true时，表示拦截此请求。 > **说明：** > > - 重定向后的URL无法单独拦截。如需拦截，必须同时对原始请求URL进行拦截。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandler-onRequestStart(      callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void--><!--Device-WebSchemeHandler-onRequestStart(      callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (request: WebSchemeHandlerRequest, handler: WebResourceHandler) =&gt; boolean | 是 | 拦截对应scheme请求开始时触发的回调。request为请求，handler用于提供自定义的返回头以及返回体给Web组件，返回值true表示拦截此请求，false 表示不拦截此请求，handler失效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## onRequestStop

```TypeScript
onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void
```

当请求完成时的回调，仅当 onRequestStart 回调决定拦截此请求时触发。触发的时机有以下两点： 1. WebResourceHandler调用didFail或者didFinish。 2. 此请求因为其他原因中断（如网络错误、系统异常等）。

**起始版本：** 12

**ArkTS模式：** 起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebSchemeHandler-onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void--><!--Device-WebSchemeHandler-onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md)&gt; | 是 | 对应请求结束的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |

