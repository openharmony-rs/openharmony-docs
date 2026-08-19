# FirstScreenPaint

提供首屏渲染事件的信息，包括URL和绘制时间。适用于需要监控页面首屏渲染性能的场景，提升性能优化的准确性和用户体验。

**起始版本：** 23

<!--Device-unnamed-declare interface FirstScreenPaint--><!--Device-unnamed-declare interface FirstScreenPaint-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## firstScreenPaintTime

```TypeScript
firstScreenPaintTime: number
```

url所指页面首屏绘制完成的时刻。 单位：毫秒。

**类型：** number

**起始版本：** 23

<!--Device-FirstScreenPaint-firstScreenPaintTime: number--><!--Device-FirstScreenPaint-firstScreenPaintTime: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## navigationStartTime

```TypeScript
navigationStartTime: number
```

url所指页面开始导航的时刻。 单位：毫秒。

**类型：** number

**起始版本：** 23

<!--Device-FirstScreenPaint-navigationStartTime: number--><!--Device-FirstScreenPaint-navigationStartTime: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

本次首屏渲染统计所对应的url。

**类型：** string

**起始版本：** 23

<!--Device-FirstScreenPaint-url: string--><!--Device-FirstScreenPaint-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

