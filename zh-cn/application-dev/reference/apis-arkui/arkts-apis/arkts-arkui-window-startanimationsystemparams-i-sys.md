# StartAnimationSystemParams（系统接口）

启动动画配置，仅对全屏应用生效。

不同应用间跳转场景不生效，仍保持系统默认动效。

**起始版本：** 20

<!--Device-window-interface StartAnimationSystemParams--><!--Device-window-interface StartAnimationSystemParams-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationConfig

```TypeScript
animationConfig?: WindowAnimationConfig
```

窗口动画参数配置。默认动画曲线为WindowAnimationCurve.LINEAR，duration为0。

**类型：** WindowAnimationConfig

**起始版本：** 20

<!--Device-StartAnimationSystemParams-animationConfig?: WindowAnimationConfig--><!--Device-StartAnimationSystemParams-animationConfig?: WindowAnimationConfig-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: AnimationType
```

窗口动画类型。

**类型：** AnimationType

**起始版本：** 20

<!--Device-StartAnimationSystemParams-type: AnimationType--><!--Device-StartAnimationSystemParams-type: AnimationType-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

