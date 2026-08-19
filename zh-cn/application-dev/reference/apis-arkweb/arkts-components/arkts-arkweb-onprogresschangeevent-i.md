# OnProgressChangeEvent

定义网页加载进度变化时触发的回调信息，包括新的进度值。适用于需要监控页面加载进度的场景，提升加载过程的可见性和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface OnProgressChangeEvent--><!--Device-unnamed-declare interface OnProgressChangeEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## newProgress

```TypeScript
newProgress: number
```

新的加载进度，取值范围为[0, 100]的整数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnProgressChangeEvent-newProgress: number--><!--Device-OnProgressChangeEvent-newProgress: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

