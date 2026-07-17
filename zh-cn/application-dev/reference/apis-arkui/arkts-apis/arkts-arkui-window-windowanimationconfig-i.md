# WindowAnimationConfig

窗口动画参数配置。

**起始版本：** 20

<!--Device-window-interface WindowAnimationConfig--><!--Device-window-interface WindowAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## curve

```TypeScript
curve: WindowAnimationCurve
```

动画曲线类型。

**类型：** WindowAnimationCurve

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-curve: WindowAnimationCurve--><!--Device-WindowAnimationConfig-curve: WindowAnimationCurve-End-->

**系统能力：** SystemCapability.Window.SessionManager

## duration

```TypeScript
duration?: number
```

动画播放的时长，单位毫秒（ms）。

默认值：0，最大值：3000。

根据动画曲线类型决定是否必填。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-duration?: long--><!--Device-WindowAnimationConfig-duration?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## param

```TypeScript
param?: WindowAnimationCurveParam
```

动画曲线参数，根据动画曲线类型决定是否必填。

**类型：** WindowAnimationCurveParam

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WindowAnimationConfig-param?: WindowAnimationCurveParam--><!--Device-WindowAnimationConfig-param?: WindowAnimationCurveParam-End-->

**系统能力：** SystemCapability.Window.SessionManager

