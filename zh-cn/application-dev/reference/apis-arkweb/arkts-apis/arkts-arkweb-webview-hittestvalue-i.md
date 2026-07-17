# HitTestValue

提供点击区域的元素信息。示例代码参考[getLastHitTest](arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest-1).

**起始版本：** 9

<!--Device-webview-interface HitTestValue--><!--Device-webview-interface HitTestValue-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## extra

```TypeScript
extra: string
```

点击区域的附加参数信息。若被点击区域为图片或链接，则附加参数信息为其url地址。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HitTestValue-extra: string--><!--Device-HitTestValue-extra: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: WebHitTestType
```

当前被点击区域的元素类型。

**类型：** WebHitTestType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HitTestValue-type: WebHitTestType--><!--Device-HitTestValue-type: WebHitTestType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

