# WindowMode

启动UIAbility时窗口的创建模式，类型为枚举。可配合[startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)方法使用。

**起始版本：** 12

<!--Device-AbilityConstant-export enum WindowMode--><!--Device-AbilityConstant-export enum WindowMode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_FULLSCREEN

```TypeScript
WINDOW_MODE_FULLSCREEN = 1
```

全屏模式。仅在2in1和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowMode-WINDOW_MODE_FULLSCREEN = 1--><!--Device-WindowMode-WINDOW_MODE_FULLSCREEN = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_PRIMARY

```TypeScript
WINDOW_MODE_SPLIT_PRIMARY = 100
```

支持应用内拉起Ability时设置为分屏，左侧分屏。仅在折叠屏和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowMode-WINDOW_MODE_SPLIT_PRIMARY = 100--><!--Device-WindowMode-WINDOW_MODE_SPLIT_PRIMARY = 100-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## WINDOW_MODE_SPLIT_SECONDARY

```TypeScript
WINDOW_MODE_SPLIT_SECONDARY = 101
```

支持应用内拉起Ability时设置为分屏，右侧分屏。仅在折叠屏和Tablet设备上生效。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowMode-WINDOW_MODE_SPLIT_SECONDARY = 101--><!--Device-WindowMode-WINDOW_MODE_SPLIT_SECONDARY = 101-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

