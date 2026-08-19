# OnOverScrollEvent

定义网页过度滚动时触发的回调信息，包括水平和垂直偏移量。

**起始版本：** 12

<!--Device-unnamed-declare interface OnOverScrollEvent--><!--Device-unnamed-declare interface OnOverScrollEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## xOffset

```TypeScript
xOffset: number
```

以网页最左端为基准，水平过度滚动的偏移量。 单位：vp。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnOverScrollEvent-xOffset: number--><!--Device-OnOverScrollEvent-xOffset: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## yOffset

```TypeScript
yOffset: number
```

以网页最上端为基准，竖直过度滚动的偏移量。 单位：vp。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnOverScrollEvent-yOffset: number--><!--Device-OnOverScrollEvent-yOffset: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

