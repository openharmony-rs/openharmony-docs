# FloatViewLimits

标准悬浮窗窗口的限制。

**起始版本：** 26.0.0

<!--Device-floatView-interface FloatViewLimits--><!--Device-floatView-interface FloatViewLimits-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## maxSize

```TypeScript
maxSize: window.Size
```

标准悬浮窗的最大尺寸。

**类型：** window.Size

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewLimits-maxSize: window.Size--><!--Device-FloatViewLimits-maxSize: window.Size-End-->

**系统能力：** SystemCapability.Window.SessionManager

## minSize

```TypeScript
minSize: window.Size
```

标准悬浮窗的最小尺寸。

**类型：** window.Size

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewLimits-minSize: window.Size--><!--Device-FloatViewLimits-minSize: window.Size-End-->

**系统能力：** SystemCapability.Window.SessionManager

## ratioLimits

```TypeScript
ratioLimits: Array<RatioLimit>
```

标准悬浮窗的宽高比限制范围。

**类型：** Array<RatioLimit>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FloatViewLimits-ratioLimits: Array<RatioLimit>--><!--Device-FloatViewLimits-ratioLimits: Array<RatioLimit>-End-->

**系统能力：** SystemCapability.Window.SessionManager

