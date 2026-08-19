# NativeEmbedTouchInfo

提供手指触摸同层标签的详细信息，包括标签ID和触摸事件。适用于需要处理同层元素触摸交互的场景，提升触摸体验的定制性和灵活性。

**起始版本：** 11

<!--Device-unnamed-declare interface NativeEmbedTouchInfo--><!--Device-unnamed-declare interface NativeEmbedTouchInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## embedId

```TypeScript
embedId?: string
```

同层标签的唯一id。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedTouchInfo-embedId?: string--><!--Device-NativeEmbedTouchInfo-embedId?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result?: EventResult
```

通知Web组件手势事件的消费结果。

**类型：** [EventResult](arkts-arkweb-eventresult-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedTouchInfo-result?: EventResult--><!--Device-NativeEmbedTouchInfo-result?: EventResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## touchEvent

```TypeScript
touchEvent?: TouchEvent
```

手指触摸动作信息。

**类型：** TouchEvent

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedTouchInfo-touchEvent?: TouchEvent--><!--Device-NativeEmbedTouchInfo-touchEvent?: TouchEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

