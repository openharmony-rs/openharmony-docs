# WindowLayoutInfo

窗口布局信息。

**起始版本：** 23

<!--Device-window-interface WindowLayoutInfo--><!--Device-window-interface WindowLayoutInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatingBall } from '@kit.ArkUI';
import { floatView } from '@kit.ArkUI';
import { window } from '@kit.ArkUI';
```

## windowAlpha

```TypeScript
windowAlpha?: double
```

窗口透明度。有效值范围为[0.0, 1.0]，0.0表示完全透明，1.0表示完全不透明。默认值是-1.0，表示未查询到窗口透明度或者查询失败。

**类型：** double

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WindowLayoutInfo-windowAlpha?: double--><!--Device-WindowLayoutInfo-windowAlpha?: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

窗口尺寸，窗口在屏幕上的实际位置和大小。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WindowLayoutInfo-windowRect: Rect--><!--Device-WindowLayoutInfo-windowRect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

