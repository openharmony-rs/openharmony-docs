# ScreenCaptureHandler

Defines the onScreenCapture callback, related to {@link onScreenCapture} method.

**起始版本：** 10

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

Reject the request.

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## getOrigin

```TypeScript
getOrigin(): string
```

Gets the source of the webpage that attempted to access the restricted resource.

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | @syscap SystemCapability.Web.Webview.Core@atomicservice |

## grant

```TypeScript
grant(config: ScreenCaptureConfig): void
```

Grant origin access to a given resource.

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | ScreenCaptureConfig | 是 | The screen capture configuration. |

