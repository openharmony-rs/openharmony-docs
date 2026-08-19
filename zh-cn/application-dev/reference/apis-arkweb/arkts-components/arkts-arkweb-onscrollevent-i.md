# OnScrollEvent

定义滚动条滑动到指定位置时触发的回调信息，包括水平和垂直偏移量。

**起始版本：** 12

<!--Device-unnamed-declare interface OnScrollEvent--><!--Device-unnamed-declare interface OnScrollEvent-End-->

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

以网页最左端为基准，水平滚动条滚动所在位置。 单位：vp。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnScrollEvent-xOffset: number--><!--Device-OnScrollEvent-xOffset: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## yOffset

```TypeScript
yOffset: number
```

以网页最上端为基准，竖直滚动条滚动所在位置。 单位：vp。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnScrollEvent-yOffset: number--><!--Device-OnScrollEvent-yOffset: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

