# SslErrorHandler

Defines the ssl error request result, related to {@link onSslErrorEventReceive} method.

**起始版本：** 9

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

取消此请求。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(abortLoading: boolean): void
```

ArkWeb遇到了SSL证书错误，该接口表示是否终止或者继续展示错误给用户。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abortLoading | boolean | 是 | 如果abortLoading为true，则取消当前请求并停留在当前页面，如果为false，则拒绝忽略该SSL错误，最终展示空白页，如果开启了默认错误页，则显示默认错误页。默认为false |

## handleConfirm

```TypeScript
handleConfirm(): void
```

继续使用SSL证书。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

