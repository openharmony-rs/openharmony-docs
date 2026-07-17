# TransitionAnimation

窗口转场动画配置。

**起始版本：** 20

<!--Device-window-interface TransitionAnimation--><!--Device-window-interface TransitionAnimation-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## config

```TypeScript
config: WindowAnimationConfig
```

本次转场动画配置。

**类型：** WindowAnimationConfig

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TransitionAnimation-config: WindowAnimationConfig--><!--Device-TransitionAnimation-config: WindowAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

## opacity

```TypeScript
opacity?: number
```

不透明度，转场动画作用的窗口属性，值为0时窗口完全透明，默认值为1.0。当动画类型为WindowTransitionType.DESTROY时，代表动画终点的不透明度。取值范围0~1.0，在动画结束时恢复为1.0。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TransitionAnimation-opacity?: double--><!--Device-TransitionAnimation-opacity?: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

