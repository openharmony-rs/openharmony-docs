# WindowAnchorInfo（系统接口）

一级子窗与主窗保持相对位置的窗口锚点参数信息。

**起始版本：** 24

<!--Device-window-interface WindowAnchorInfo--><!--Device-window-interface WindowAnchorInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## anchorType

```TypeScript
anchorType: WindowAnchor
```

一级子窗与主窗保持相对位置不变时的窗口锚点枚举。

**类型：** WindowAnchor

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnchorInfo-anchorType: WindowAnchor--><!--Device-WindowAnchorInfo-anchorType: WindowAnchor-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## offsetX

```TypeScript
offsetX?: number
```

一级子窗锚点与主窗锚点位置的X轴偏移量，单位为px。仅支持整数输入，浮点数向下取整，默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnchorInfo-offsetX?: int--><!--Device-WindowAnchorInfo-offsetX?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## offsetY

```TypeScript
offsetY?: number
```

一级子窗锚点与主窗锚点位置的Y轴偏移量，单位为px。仅支持整数输入，浮点数向下取整，默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnchorInfo-offsetY?: int--><!--Device-WindowAnchorInfo-offsetY?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

