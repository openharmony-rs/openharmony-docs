# PreviewMenuOptions

用于配置预览菜单选项，支持设置菜单弹出时的振动效果。适用于需要增强菜单交互反馈的场景，提升用户体验。

**起始版本：** 20

<!--Device-unnamed-declare interface PreviewMenuOptions--><!--Device-unnamed-declare interface PreviewMenuOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## hapticFeedbackMode

```TypeScript
hapticFeedbackMode?: HapticFeedbackMode
```

菜单弹出时振动效果。需配置"ohos.permission.VIBRATE"权限 默认值：HapticFeedbackMode.DISABLED，菜单弹出时不振动。

**类型：** HapticFeedbackMode

**默认值：** HapticFeedbackMode.DISABLED

**起始版本：** 20

<!--Device-PreviewMenuOptions-hapticFeedbackMode?: HapticFeedbackMode--><!--Device-PreviewMenuOptions-hapticFeedbackMode?: HapticFeedbackMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

