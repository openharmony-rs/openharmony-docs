# WindowCreateParams

```TypeScript
interface WindowCreateParams
```

应用启动时的窗口参数配置。

**起始版本：** 20

<!--Device-window-interface WindowCreateParams--><!--Device-window-interface WindowCreateParams-End-->

**系统能力：** SystemCapability.Window.SessionManager

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationParams

```TypeScript
animationParams?: StartAnimationParams
```

The params of start animation

**类型：** [StartAnimationParams](arkts-arkui-window-startanimationparams-i.md)

**起始版本：** 20

<!--Device-WindowCreateParams-animationParams?: StartAnimationParams--><!--Device-WindowCreateParams-animationParams?: StartAnimationParams-End-->

**系统能力：** SystemCapability.Window.SessionManager

## excludeFromDock

```TypeScript
excludeFromDock?: boolean
```

是否屏蔽快捷栏图标及Hover缩略图。如果为true，则当前窗口不会在快捷栏上显示图标及Hover缩略图。该参数只在同应用内生效，只适用于PC/2in1设备，并且需绑定托盘图标。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowCreateParams-excludeFromDock?: boolean--><!--Device-WindowCreateParams-excludeFromDock?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## excludeFromRecent

```TypeScript
excludeFromRecent?: boolean
```

是否屏蔽多任务视图。如果为true，则当前窗口不会在多任务视图中显示。该参数只在同应用内生效，只适用于PC/2in1设备，并且需绑定托盘图标。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowCreateParams-excludeFromRecent?: boolean--><!--Device-WindowCreateParams-excludeFromRecent?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## minimizeOnStart

```TypeScript
minimizeOnStart?: boolean
```

窗口是否以最小化状态启动。如果为true，窗口将不会拉起到前台，只会在快捷栏上显示图标。该参数只在同应用内生效，只适用于PC/2in1设备。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowCreateParams-minimizeOnStart?: boolean--><!--Device-WindowCreateParams-minimizeOnStart?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## needAnimation

```TypeScript
needAnimation?: boolean
```

窗口拉起时是否需要动画

默认跟随产品配置，例如PC设备上拉起主窗默认有动画，Phone上拉起子窗默认无动画。当产品支持配置，跟随开发者设置的值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowCreateParams-needAnimation?: boolean--><!--Device-WindowCreateParams-needAnimation?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager
