# FloatViewRectChangeInfo

标准悬浮窗矩形区域变化信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## reason

```TypeScript
reason: string
```

标准悬浮窗矩形区域变化的原因。原因和对应含义如下：

"POSITION_CHANGE"：位置变化

"SIZE_CHANGE"：大小变化

"RECT_CHANGE"：位置大小同时变化

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: window.Rect
```

标准悬浮窗窗口矩形区域。

**类型：** [window.Rect](arkts-arkui-window-rect-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowScale

```TypeScript
windowScale: number
```

标准悬浮窗窗口缩放比例。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager
