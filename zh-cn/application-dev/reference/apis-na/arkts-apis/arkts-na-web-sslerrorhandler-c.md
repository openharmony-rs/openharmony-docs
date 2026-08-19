# SslErrorHandler

Defines the ssl error request result, related to onSslErrorEventReceive method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class SslErrorHandler--><!--Device-unnamed-export declare class SslErrorHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SslErrorHandler-constructor()--><!--Device-SslErrorHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

Cancel this request.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SslErrorHandler-handleCancel(): void--><!--Device-SslErrorHandler-handleCancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(abortLoading: boolean): void
```

ArkWeb has encountered an SSL certificate error, and this interface indicates whether to terminate or continue displaying the error to users.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SslErrorHandler-handleCancel(abortLoading: boolean): void--><!--Device-SslErrorHandler-handleCancel(abortLoading: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abortLoading | boolean | 是 | If abortLoading is true, the current request will be canceled and the user will remain on the current page. If it is false, the SSL error will not be ignored, and a blank page will be displayed. If a default error page is enabled, the default error page will be shown instead. The default value is false. |

## handleConfirm

```TypeScript
handleConfirm(): void
```

Confirm to use the SSL certificate.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-SslErrorHandler-handleConfirm(): void--><!--Device-SslErrorHandler-handleConfirm(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

