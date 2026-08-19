# OnPageVisibleEvent

定义旧页面不再呈现，新页面即将可见时触发的回调函数。

**起始版本：** 12

<!--Device-unnamed-declare interface OnPageVisibleEvent--><!--Device-unnamed-declare interface OnPageVisibleEvent-End-->

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

新页面的URL地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnPageVisibleEvent-url: string--><!--Device-OnPageVisibleEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

