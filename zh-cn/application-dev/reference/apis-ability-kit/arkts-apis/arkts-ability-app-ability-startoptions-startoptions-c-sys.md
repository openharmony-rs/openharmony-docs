# StartOptions

StartOptions可以作为启动UIAbility接口（例如[startAbility()](arkts-ability-uiabilitycontext-c.md#startability-2)）的入参，用于指定目标UIAbility启动时的选项，包括但不局限于窗口模式、目标UIAbility启动时所在的屏幕等。

**起始版本：** 9

<!--Device-unnamed-declare class StartOptions--><!--Device-unnamed-declare class StartOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { StartOptions } from '@kit.AbilityKit';
```

## windowFocused

```TypeScript
windowFocused?: boolean
```

窗口是否获焦。默认是true，表示窗口获焦。

**约束：**

1.该功能仅在2in1和Tablet设备上生效。

2.仅在[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)中生效。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartOptions-windowFocused?: boolean--><!--Device-StartOptions-windowFocused?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

