# AdsBlockedDetails

发生广告拦截时，广告资源信息。

**起始版本：** 12

<!--Device-unnamed-declare interface AdsBlockedDetails--><!--Device-unnamed-declare interface AdsBlockedDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## adsBlocked

```TypeScript
adsBlocked: Array<string>
```

被过滤的资源的url或dompath标识，被过滤的多个对象url相同则可能出现重复元素。

**类型：** Array&lt;string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockedDetails-adsBlocked: Array<string>--><!--Device-AdsBlockedDetails-adsBlocked: Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

发生广告过滤的页面url。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockedDetails-url: string--><!--Device-AdsBlockedDetails-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

