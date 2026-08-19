# WebKeyboardCallbackInfo

拦截网页可编辑元素拉起软键盘的回调入参，包括WebKeyboardController和可编辑元素的属性。适用于需要自定义键盘交互的场景，提升输入体验的定制性和灵活性。

**起始版本：** 12

<!--Device-unnamed-declare interface WebKeyboardCallbackInfo--><!--Device-unnamed-declare interface WebKeyboardCallbackInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## attributes

```TypeScript
attributes: Record<string, string>
```

触发本次软键盘弹出的网页元素属性。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardCallbackInfo-attributes: Record<string, string>--><!--Device-WebKeyboardCallbackInfo-attributes: Record<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebKeyboardController
```

提供控制自定义键盘的输入、删除、关闭等操作。

**类型：** [WebKeyboardController](arkts-arkweb-webkeyboardcontroller-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardCallbackInfo-controller: WebKeyboardController--><!--Device-WebKeyboardCallbackInfo-controller: WebKeyboardController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

