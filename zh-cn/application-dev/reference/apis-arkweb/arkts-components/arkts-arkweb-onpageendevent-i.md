# OnPageEndEvent

定义网页加载结束时触发的回调信息，包括页面URL。适用于需要监控页面加载完成的场景，提升页面生命周期的管理能力。

**起始版本：** 12

<!--Device-unnamed-declare interface OnPageEndEvent--><!--Device-unnamed-declare interface OnPageEndEvent-End-->

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

网页加载完成后的页面URL地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnPageEndEvent-url: string--><!--Device-OnPageEndEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

