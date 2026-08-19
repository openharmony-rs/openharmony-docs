# WebSchemeHandler

This class is used to intercept requests for a specified scheme.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class WebSchemeHandler--><!--Device-webview-class WebSchemeHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## onRequestStart

```TypeScript
onRequestStart(
        callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void
```

Callback for handling the request.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebSchemeHandler-onRequestStart(        callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void--><!--Device-WebSchemeHandler-onRequestStart(        callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (request: WebSchemeHandlerRequest, handler: WebResourceHandler) =&gt; boolean | 是 | Callback of handling the request. If callback return false, it means no interception. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |

## onRequestStop

```TypeScript
onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void
```

Callback when the request is completed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebSchemeHandler-onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void--><!--Device-WebSchemeHandler-onRequestStop(callback: Callback<WebSchemeHandlerRequest>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[WebSchemeHandlerRequest](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webschemehandlerrequest-c.md)&gt; | 是 | Callback of request is completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid input parameter. |

