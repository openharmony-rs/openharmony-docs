# AvoidArea

窗口内容的避让区域。

窗口内容做[沉浸式布局](../../../../windowmanager/window-terminology.md#沉浸式布局)适配时，需要按照[AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)对应的AvoidArea做窗口内容避让。

在避让区域内，应用窗口内容被遮挡且无法响应用户点击事件。

> **说明：**  
>  
> 示意图展示了leftRect、topRect、rightRect、bottomRect的含义。  
>  
> ![avoidArea](../../../../reference/apis-arkui/figures/avoidArea.png)

**起始版本：** 7

<!--Device-window-interface AvoidArea--><!--Device-window-interface AvoidArea-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## bottomRect

```TypeScript
bottomRect: Rect
```

中心位于窗口的两条对角线的底部的矩形区。

**类型：** Rect

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidArea-bottomRect: Rect--><!--Device-AvoidArea-bottomRect: Rect-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## leftRect

```TypeScript
leftRect: Rect
```

中心位于窗口的两条对角线的左侧的矩形区。

**类型：** Rect

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidArea-leftRect: Rect--><!--Device-AvoidArea-leftRect: Rect-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## rightRect

```TypeScript
rightRect: Rect
```

中心位于窗口的两条对角线的右侧的矩形区。

**类型：** Rect

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidArea-rightRect: Rect--><!--Device-AvoidArea-rightRect: Rect-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## topRect

```TypeScript
topRect: Rect
```

中心位于窗口的两条对角线的顶部的矩形区。

**类型：** Rect

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidArea-topRect: Rect--><!--Device-AvoidArea-topRect: Rect-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## visible

```TypeScript
visible: boolean
```

无实际意义，暂不支持使用。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidArea-visible: boolean--><!--Device-AvoidArea-visible: boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

