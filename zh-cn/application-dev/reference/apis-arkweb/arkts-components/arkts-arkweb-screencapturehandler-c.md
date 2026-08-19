# ScreenCaptureHandler

ScreenCaptureHandler 是 Web 组件提供的屏幕捕获权限处理类，用于响应网页发起的屏幕捕获请求。该类适用于在线教育、远程会议、屏幕录制等需要获取用户屏幕内容的应用场景。该类允许开发者通过 grant 或 deny 方法控制是否授予网页屏幕捕获权限，并通过 getOrigin 方法获取请求来源信息，帮助开发者在保护用户隐私的同时，灵活处理网页的屏幕捕获访问需求，提升应用的安全性和用户体验。示例代码参考 [onScreenCaptureRequest](arkts-arkweb-web-attribute.md#onscreencapturerequest)事件。 > **说明：** > > - [grant](#grant)()与 [deny](#deny)() 方法互斥，对同一个 > ScreenCaptureHandler 实例的同一请求只能调用其中一个。 > > - 调用后不应再对同一请求调用另一个方法。

**起始版本：** 10

<!--Device-unnamed-declare class ScreenCaptureHandler--><!--Device-unnamed-declare class ScreenCaptureHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

ScreenCaptureHandler的构造函数。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-constructor()--><!--Device-ScreenCaptureHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

拒绝网页发起的屏幕捕获操作。用于用户选择不允许，或出于安全原因需要阻止屏幕捕获时调用。调用后将终止当前的屏幕捕获请求，系统会通知网页屏幕捕获权限被拒绝。拒绝操作不影响后续新的屏幕捕获请求。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-deny(): void--><!--Device-ScreenCaptureHandler-deny(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getOrigin

```TypeScript
getOrigin(): string
```

获取网页来源。用于验证请求来源的可信度，或实现白名单机制以控制哪些网页可以进行屏幕捕获。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-getOrigin(): string--><!--Device-ScreenCaptureHandler-getOrigin(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前发起屏幕捕获请求的网页的来源。 |

## grant

```TypeScript
grant(config: ScreenCaptureConfig): void
```

对网页访问的屏幕捕获操作进行授权。该方法会根据提供的配置参数授予屏幕捕获权限，授权后网页可以按照配置的参数进行屏幕捕获。配置参数会被验证，确保符合系统安全要求。用于用户同意网页的屏幕捕获请求后调用，或根据业务策略自动授权可信网页时 使用。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void--><!--Device-ScreenCaptureHandler-grant(config: ScreenCaptureConfig): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ScreenCaptureConfig](arkts-arkweb-screencaptureconfig-i.md) | 是 | 屏幕捕获配置，用于设置屏幕捕获的相关参数。 |

