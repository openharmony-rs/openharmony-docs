# OnPageBeginEvent

定义网页加载开始时触发的回调信息，包括页面URL。适用于需要监控页面加载开始的场景，提升页面生命周期的管理能力。

**起始版本：** 12

<!--Device-unnamed-declare interface OnPageBeginEvent--><!--Device-unnamed-declare interface OnPageBeginEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## url

```TypeScript
url: string
```

网页加载开始时即将加载的页面URL地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnPageBeginEvent-url: string--><!--Device-OnPageBeginEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

