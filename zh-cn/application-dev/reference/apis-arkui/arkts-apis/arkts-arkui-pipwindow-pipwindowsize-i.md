# PiPWindowSize

画中画窗口大小。

**起始版本：** 15

<!--Device-PiPWindow-interface PiPWindowSize--><!--Device-PiPWindow-interface PiPWindowSize-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## height

```TypeScript
height: number
```

窗口高度，单位为px，该参数应为正整数，不大于屏幕高度。

**类型：** number

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindowSize-height: int--><!--Device-PiPWindowSize-height: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## scale

```TypeScript
scale: number
```

窗口缩放比，显示大小相对于width和height的缩放比，该参数为浮点数，取值范围大于0.0，小于等于1.0。等于1表示与width和height一样大。

**类型：** number

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindowSize-scale: double--><!--Device-PiPWindowSize-scale: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

## width

```TypeScript
width: number
```

窗口宽度，单位为px，该参数应为正整数，不大于屏幕宽度。

**类型：** number

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindowSize-width: int--><!--Device-PiPWindowSize-width: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

