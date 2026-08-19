# OnResourceLoadEvent

定义加载URL时触发的回调信息，包括资源URL。适用于需要监控资源加载行为的场景，提升资源管理的可见性和性能优化。

**起始版本：** 12

<!--Device-unnamed-declare interface OnResourceLoadEvent--><!--Device-unnamed-declare interface OnResourceLoadEvent-End-->

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

所加载的资源文件url信息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnResourceLoadEvent-url: string--><!--Device-OnResourceLoadEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

