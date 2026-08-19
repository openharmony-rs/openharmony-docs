# WindowFeatures

提供网页请求创建的新窗口特征信息，包括大小和位置。适用于需要精确控制新窗口属性的场景，提升窗口布局的准确性和用户体验。

**起始版本：** 23

<!--Device-unnamed-declare interface WindowFeatures--><!--Device-unnamed-declare interface WindowFeatures-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## height

```TypeScript
height: number
```

新窗口高度（单位：像素）。

**类型：** number

**起始版本：** 23

<!--Device-WindowFeatures-height: number--><!--Device-WindowFeatures-height: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## width

```TypeScript
width: number
```

新窗口宽度（单位：像素）。

**类型：** number

**起始版本：** 23

<!--Device-WindowFeatures-width: number--><!--Device-WindowFeatures-width: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## x

```TypeScript
x: number
```

新窗口左上角横坐标（单位：像素）。

**类型：** number

**起始版本：** 23

<!--Device-WindowFeatures-x: number--><!--Device-WindowFeatures-x: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## y

```TypeScript
y: number
```

新窗口左上角纵坐标（单位：像素）。

**类型：** number

**起始版本：** 23

<!--Device-WindowFeatures-y: number--><!--Device-WindowFeatures-y: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

