# ScreenCaptureHandler

Defines the onScreenCapture callback, related to onScreenCapture method.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class ScreenCaptureHandler--><!--Device-unnamed-export declare class ScreenCaptureHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebKeyboardController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScreenCaptureHandler-constructor()--><!--Device-ScreenCaptureHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

Reject the request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ScreenCaptureHandler-deny(): void--><!--Device-ScreenCaptureHandler-deny(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getOrigin

```TypeScript
getOrigin(): string
```

Gets the source of the webpage that attempted to access the restricted resource.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

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

**废弃版本：** -1

<!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void--><!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ScreenCaptureConfig](arkts-na-web-screencaptureconfig-i.md) | 是 | The screen capture configuration. |

