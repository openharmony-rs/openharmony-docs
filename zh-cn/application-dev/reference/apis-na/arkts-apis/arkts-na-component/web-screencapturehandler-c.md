# ScreenCaptureHandler

Defines the onScreenCapture callback, related to \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ method.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ScreenCaptureHandler--><!--Device-unnamed-export declare class ScreenCaptureHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebKeyboardController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureHandler-constructor()--><!--Device-ScreenCaptureHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

Reject the request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureHandler-deny(): void--><!--Device-ScreenCaptureHandler-deny(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getOrigin

```TypeScript
getOrigin(): string
```

Gets the source of the webpage that attempted to access the restricted resource.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureHandler-getOrigin(): string--><!--Device-ScreenCaptureHandler-getOrigin(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string |  |

## grant

```TypeScript
grant(config: ScreenCaptureConfig): void
```

Grant origin access to a given resource.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void--><!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The screen capture configuration. |

