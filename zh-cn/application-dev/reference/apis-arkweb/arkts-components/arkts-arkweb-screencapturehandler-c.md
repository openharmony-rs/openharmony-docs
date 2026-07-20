# ScreenCaptureHandler

Defines the onScreenCapture callback, related to {@link onScreenCapture} method.

**起始版本：** 10

<!--Device-unnamed-declare class ScreenCaptureHandler--><!--Device-unnamed-declare class ScreenCaptureHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-constructor()--><!--Device-ScreenCaptureHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="deny"></a>
## deny

```TypeScript
deny(): void
```

Reject the request.

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-deny(): void--><!--Device-ScreenCaptureHandler-deny(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="getorigin"></a>
## getOrigin

```TypeScript
getOrigin(): string
```

Gets the source of the webpage that attempted to access the restricted resource.

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-getOrigin(): string--><!--Device-ScreenCaptureHandler-getOrigin(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | @syscap SystemCapability.Web.Webview.Core@atomicservice |

<a id="grant"></a>
## grant

```TypeScript
grant(config: ScreenCaptureConfig): void
```

Grant origin access to a given resource.

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void--><!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ScreenCaptureConfig](arkts-arkweb-screencaptureconfig-i.md) | 是 | The screen capture configuration. |

