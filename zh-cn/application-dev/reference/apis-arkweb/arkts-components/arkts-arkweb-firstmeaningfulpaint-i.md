# FirstMeaningfulPaint

提供网页绘制页面主要内容的详细信息，包括导航时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface FirstMeaningfulPaint--><!--Device-unnamed-declare interface FirstMeaningfulPaint-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## firstMeaningfulPaintTime

```TypeScript
firstMeaningfulPaintTime?: number
```

绘制页面主要内容时间，单位以毫秒表示。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FirstMeaningfulPaint-firstMeaningfulPaintTime?: number--><!--Device-FirstMeaningfulPaint-firstMeaningfulPaintTime?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## navigationStartTime

```TypeScript
navigationStartTime?: number
```

导航条加载时间，单位以微秒表示。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FirstMeaningfulPaint-navigationStartTime?: number--><!--Device-FirstMeaningfulPaint-navigationStartTime?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

