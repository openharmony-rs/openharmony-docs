# IntelligentTrackingPreventionDetails

提供智能防跟踪拦截的详细信息，包括网站域名和追踪者域名。适用于需要监控广告拦截行为的场景，提升隐私保护的透明度和可控性。

**起始版本：** 12

<!--Device-unnamed-declare interface IntelligentTrackingPreventionDetails--><!--Device-unnamed-declare interface IntelligentTrackingPreventionDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## host

```TypeScript
host: string
```

网站域名。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IntelligentTrackingPreventionDetails-host: string--><!--Device-IntelligentTrackingPreventionDetails-host: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## trackerHost

```TypeScript
trackerHost: string
```

追踪者域名。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IntelligentTrackingPreventionDetails-trackerHost: string--><!--Device-IntelligentTrackingPreventionDetails-trackerHost: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

