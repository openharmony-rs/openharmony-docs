# OnLoadInterceptEvent

定义截获资源加载时触发的回调信息，包括请求详情。适用于需要拦截或处理资源加载的场景，提升资源控制的灵活性和安全性。

**起始版本：** 12

<!--Device-unnamed-declare interface OnLoadInterceptEvent--><!--Device-unnamed-declare interface OnLoadInterceptEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## data

```TypeScript
data: WebResourceRequest
```

url请求的相关信息。

**类型：** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnLoadInterceptEvent-data: WebResourceRequest--><!--Device-OnLoadInterceptEvent-data: WebResourceRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

