# @ohos.app.ability.abilityLifecycleCallback (UIAbility生命周期回调监听器)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy; @xuzhihao666-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

[UIAbility](js-apis-app-ability-uiAbility.md)从创建到销毁过程其生命周期是动态变化的。AbilityLifecycleCallback模块提供监听[UIAbility](js-apis-app-ability-uiAbility.md)生命周期变化的能力，可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 本模块接口只能监听进程内UIAbility生命周期变化。

## 使用说明

1. 应用创建AbilityLifecycleCallback对象，并调用[ApplicationContext.on('abilityLifecycle')](js-apis-inner-application-applicationContext.md#applicationcontextonabilitylifecycle)接口注册UIAbility生命周期变化监听。
2. 当UIAbility生命周期变化时，应用可以通过已注册的AbilityLifecycleCallback对象接收到UIAbility生命周期的变化通知。
3. 当应用不需要监听UIAbility生命周期变化时，需要通过[ApplicationContext.off('abilityLifecycle')](js-apis-inner-application-applicationContext.md#applicationcontextoffabilitylifecycle)接口取消监听。

## 导入模块

```ts
import { AbilityLifecycleCallback } from '@kit.AbilityKit';
```

## 属性

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 名称                     | 类型                                                        | 只读 | 可选 | 说明                                                         |
| ------------------------ | ----------------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| onAbilityWillCreate      | [OnAbilityWillCreateFn](#onabilitywillcreatefn23)           | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onCreate](js-apis-app-ability-uiAbility.md#oncreate)触发前回调。 |
| onWindowStageWillCreate  | [OnWindowStageWillCreateFn](#onwindowstagewillcreatefn23)   | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageCreate](js-apis-app-ability-uiAbility.md#onwindowstagecreate)触发前回调。 |
| onWillNewWant            | [OnWillNewWantFn](#onwillnewwantfn23)                       | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发前回调。 |
| onNewWant                | [OnNewWantFn](#onnewwantfn23)                               | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发后回调。 |
| onWindowStageWillDestroy | [OnWindowStageWillDestroyFn](#onwindowstagewilldestroyfn23) | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageDestroy](js-apis-app-ability-uiAbility.md#onwindowstagedestroy)触发前回调。 |
| onAbilityWillDestroy     | [OnAbilityWillDestroyFn](#onabilitywilldestroyfn23)         | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onDestroy](js-apis-app-ability-uiAbility.md#ondestroy)触发前回调。 |
| onAbilityWillForeground  | [OnAbilityWillForegroundFn](#onabilitywillforegroundfn23)   | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onForeground](js-apis-app-ability-uiAbility.md#onforeground)触发前回调。 |
| onAbilityWillBackground  | [OnAbilityWillBackgroundFn](#onabilitywillbackgroundfn23)   | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onBackground](js-apis-app-ability-uiAbility.md#onbackground)触发前回调。 |
| onWindowStageWillRestore | [OnWindowStageWillRestoreFn](#onwindowstagewillrestorefn23) | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发前回调。 |
| onWindowStageRestore     | [OnWindowStageRestoreFn](#onwindowstagerestorefn23)         | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发后回调。 |
| onAbilityWillSaveState   | [OnAbilityWillSaveStateFn](#onabilitywillsavestatefn23)     | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发前回调。 |
| onAbilitySaveState       | [OnAbilitySaveStateFn](#onabilitysavestatefn23)             | 否   | 是   | 注册监听应用上下文的生命周期后，在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发后回调。 |

## AbilityLifecycleCallback

### onAbilityCreate

onAbilityCreate(ability: UIAbility): void

在UIAbility的[onCreate](js-apis-app-ability-uiAbility.md#oncreate)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageCreate

onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageCreate](js-apis-app-ability-uiAbility.md#onwindowstagecreate)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageActive

onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility主窗获焦时触发回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageInactive

onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility主窗失焦时触发回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageDestroy

onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageDestroy](js-apis-app-ability-uiAbility.md#onwindowstagedestroy)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityDestroy

onAbilityDestroy(ability: UIAbility): void

在UIAbility的[onDestroy](js-apis-app-ability-uiAbility.md#ondestroy)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityForeground

onAbilityForeground(ability: UIAbility): void

在UIAbility的[onForeground](js-apis-app-ability-uiAbility.md#onforeground)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityBackground

onAbilityBackground(ability: UIAbility): void

在UIAbility的[onBackground](js-apis-app-ability-uiAbility.md#onbackground)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityContinue

onAbilityContinue(ability: UIAbility): void

在UIAbility的[onContinue](js-apis-app-ability-uiAbility.md#oncontinue)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillCreate<sup>12+</sup>

onAbilityWillCreate?(ability: UIAbility): void

在UIAbility的[onCreate](js-apis-app-ability-uiAbility.md#oncreate)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageWillCreate<sup>12+</sup>

onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageCreate](js-apis-app-ability-uiAbility.md#onwindowstagecreate)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageWillDestroy<sup>12+</sup>

onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageDestroy](js-apis-app-ability-uiAbility.md#onwindowstagedestroy)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillForeground<sup>12+</sup>

onAbilityWillForeground?(ability: UIAbility): void

在UIAbility的[onForeground](js-apis-app-ability-uiAbility.md#onforeground)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillDestroy<sup>12+</sup>

onAbilityWillDestroy?(ability: UIAbility): void

在UIAbility的[onDestroy](js-apis-app-ability-uiAbility.md#ondestroy)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillBackground<sup>12+</sup>

onAbilityWillBackground?(ability: UIAbility): void

在UIAbility的[onBackground](js-apis-app-ability-uiAbility.md#onbackground)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWillNewWant<sup>12+</sup>

onWillNewWant?(ability: UIAbility): void

在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onNewWant<sup>12+</sup>

onNewWant?(ability: UIAbility): void

在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillContinue<sup>12+</sup>

onAbilityWillContinue?(ability: UIAbility): void

在UIAbility的[onContinue](js-apis-app-ability-uiAbility.md#oncontinue)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageWillRestore<sup>12+</sup>

onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onWindowStageRestore<sup>12+</sup>

onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void

在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilityWillSaveState<sup>12+</sup>

onAbilityWillSaveState?(ability: UIAbility): void

在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发前回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### onAbilitySaveState<sup>12+</sup>

onAbilitySaveState?(ability: UIAbility): void

在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发后回调。

**原子化服务API（仅ArkTS-Dyn）**：从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillCreateFn<sup>23+</sup>

type OnAbilityWillCreateFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onCreate](js-apis-app-ability-uiAbility.md#oncreate)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnWindowStageWillCreateFn<sup>23+</sup>

type OnWindowStageWillCreateFn = (ability: UIAbility, windowStage: window.WindowStage) => void

注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageCreate](js-apis-app-ability-uiAbility.md#onwindowstagecreate)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                  |
| ----------- | ------------------------------------------------------------ | ---- | --------------------- |
| ability     | [UIAbility](js-apis-app-ability-uiAbility.md)                | 是   | 当前Ability对象。     |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是   | 当前WindowStage对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnWillNewWantFn<sup>23+</sup>

type OnWillNewWantFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnNewWantFn<sup>23+</sup>

type OnNewWantFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onNewWant](js-apis-app-ability-uiAbility.md#onnewwant)触发后回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnWindowStageWillDestroyFn<sup>23+</sup>

type OnWindowStageWillDestroyFn = (ability: UIAbility, windowStage: window.WindowStage) => void

注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageDestroy](js-apis-app-ability-uiAbility.md#onwindowstagedestroy)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                  |
| ----------- | ------------------------------------------------------------ | ---- | --------------------- |
| ability     | [UIAbility](js-apis-app-ability-uiAbility.md)                | 是   | 当前Ability对象。     |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是   | 当前WindowStage对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillDestroyFn<sup>23+</sup>

type OnAbilityWillDestroyFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onDestroy](js-apis-app-ability-uiAbility.md#ondestroy)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillForegroundFn<sup>23+</sup>

type OnAbilityWillForegroundFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onForeground](js-apis-app-ability-uiAbility.md#onforeground)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillBackgroundFn<sup>23+</sup>

type OnAbilityWillBackgroundFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onBackground](js-apis-app-ability-uiAbility.md#onbackground)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillContinueFn<sup>23+</sup>

type OnAbilityWillContinueFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在Ability迁移前触发回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnWindowStageWillRestoreFn<sup>23+</sup>

type OnWindowStageWillRestoreFn = (ability: UIAbility, windowStage: window.WindowStage) => void

注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                  |
| ----------- | ------------------------------------------------------------ | ---- | --------------------- |
| ability     | [UIAbility](js-apis-app-ability-uiAbility.md)                | 是   | 当前Ability对象。     |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是   | 当前WindowStage对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnWindowStageRestoreFn<sup>23+</sup>

type OnWindowStageRestoreFn = (ability: UIAbility, windowStage: window.WindowStage) => void

注册监听应用上下文的生命周期后，在UIAbility的[onWindowStageRestore](js-apis-app-ability-uiAbility.md#onwindowstagerestore)触发后回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                  |
| ----------- | ------------------------------------------------------------ | ---- | --------------------- |
| ability     | [UIAbility](js-apis-app-ability-uiAbility.md)                | 是   | 当前Ability对象。     |
| windowStage | [window.WindowStage](../apis-arkui/arkts-apis-window-WindowStage.md) | 是   | 当前WindowStage对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilityWillSaveStateFn<sup>23+</sup>

type OnAbilityWillSaveStateFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发前回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## OnAbilitySaveStateFn<sup>23+</sup>

type OnAbilitySaveStateFn = (ability: UIAbility) => void

注册监听应用上下文的生命周期后，在UIAbility的[onSaveState](js-apis-app-ability-uiAbility.md#onsavestate)触发后回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                          | 必填 | 说明              |
| ------- | --------------------------------------------- | ---- | ----------------- |
| ability | [UIAbility](js-apis-app-ability-uiAbility.md) | 是   | 当前Ability对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

### AbilityLifecycleCallback使用示例

本示例展示了生命周期监听机制的部分使用场景：

1. 在[AbilityStage](../../application-models/abilitystage.md)创建时注册监听。
2. 在[AbilityStage](../../application-models/abilitystage.md)销毁时注销监听。
3. 监听到对应UIAbility创建时加载资源，监听到对应UIAbility销毁时释放资源。
4. 在UIAbility创建、销毁及前后台状态切换时，记录事件并向外发送通知。

**示例：**

ArkTS-Dyn示例：

```ts
// 以MyStage.ets文件为例，使用AbilityLifecycleCallback监听UIAbility生命周期
import { AbilityLifecycleCallback, AbilityStage, application, UIAbility } from "@kit.AbilityKit";
import { hilog } from '@kit.PerformanceAnalysisKit';
import { JSON } from "@kit.ArkTS";
import { window } from "@kit.ArkUI";
import { BusinessError } from "@kit.BasicServicesKit";

const DOMAIN = 0x0000;
const TAG = 'testTag';

function loadContent() {
  // 加载数据
}

function releaseContent() {
  // 释放数据
}

function recordAbilityEvent(abilityName: string) {
  // 执行打点
}

function publishEvent() {
  // 对外发布通知
}

let abilityLifecycleCallback: AbilityLifecycleCallback = {
  onAbilityCreate(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'onAbilityCreate: ' + ability.context.abilityInfo.name);
    // UIAbility事件打点记录
    recordAbilityEvent(ability.context.abilityInfo.name);
    // 模拟入口UIAbility创建时，加载资源对外发布通知
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      loadContent();
      publishEvent();
    }
  },
  onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageCreate.');
  },
  onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageActive.');
  },
  onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageInactive.');
  },
  onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageDestroy.');
  },
  onAbilityDestroy(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'onAbilityDestroy: ' + ability.context.abilityInfo.name);
    recordAbilityEvent(ability.context.abilityInfo.name);
    // 模拟入口UIAbility销毁时，释放资源
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      releaseContent();
      publishEvent();
    }
  },
  onAbilityForeground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityForeground.');
    recordAbilityEvent(ability.context.abilityInfo.name);
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      publishEvent();
    }
  },
  onAbilityBackground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityBackground.');
    recordAbilityEvent(ability.context.abilityInfo.name);
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      publishEvent();
    }
  },
  onAbilityContinue(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityContinue.');
  },
  onNewWant(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onNewWant');
  },
  onWillNewWant(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWillNewWant');
  },
  onAbilityWillCreate(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillCreate');
  },
  onWindowStageWillCreate(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillCreate');
  },
  onWindowStageWillDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillDestroy');
  },
  onAbilityWillDestroy(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillDestroy');
  },
  onAbilityWillForeground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillForeground');
  },
  onAbilityWillBackground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillBackground');
  },
  onAbilityWillContinue(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillContinue.');
  },
  onWindowStageWillRestore(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillRestore.');
  },
  onWindowStageRestore(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageRestore.');
  },
  onAbilityWillSaveState(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillSaveState.');
  },
  onAbilitySaveState(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilitySaveState.');
  }
};

let lifecycleId = -1; // 保存监听id

export default class MyStage extends AbilityStage {
  onCreate(): void {
    hilog.info(DOMAIN, TAG, 'AbilityStage onCreate')

    // AbilityStage创建时注册UIAbility生命周期监听，并把监听id保存起来
    try {
      let applicationContext = application.getApplicationContext();
      lifecycleId = applicationContext.on('abilityLifecycle', abilityLifecycleCallback);
    } catch (e) {
      hilog.error(DOMAIN, TAG, `register abilityLifecycle failed: ${JSON.stringify(e)}`);
    }
  }

  onDestroy(): void {
    // AbilityStage销毁时取消UIAbility生命周期监听注册
    let applicationContext = application.getApplicationContext();
    applicationContext.off('abilityLifecycle', lifecycleId).catch((e: BusinessError) => {
      hilog.error(DOMAIN, TAG, `unregister abilityLifecycle failed: ${JSON.stringify(e)}`);
    });
  }
}
```

```ts
// 以EntryAbility.ets为例，展示应用入口UIAbility
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;
const TAG = 'testTag';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    hilog.info(DOMAIN, TAG, 'EntryAbility onCreate');
  }

  onDestroy(): void {
    hilog.info(DOMAIN, TAG, 'EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // 主窗创建
    hilog.info(DOMAIN, TAG, 'EntryAbility onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err) => {
      if (err.code) {
        hilog.error(DOMAIN, TAG, 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      hilog.info(DOMAIN, TAG, 'Succeeded in loading the content.');
    });
  }

  onWindowStageDestroy(): void {
    // 主窗销毁
    hilog.info(DOMAIN, TAG, 'EntryAbility onWindowStageDestroy');
  }

  onForeground(): void {
    // UIAbility切换到前台
    hilog.info(DOMAIN, TAG, 'EntryAbility onForeground');
  }

  onBackground(): void {
    // UIAbility切换到后台
    hilog.info(DOMAIN, TAG, 'EntryAbility  onBackground');
  }
}
```

ArkTS-Sta示例：

```ts
'use static'
// 以MyStage.ets文件为例，使用AbilityLifecycleCallback监听UIAbility生命周期
import { AbilityLifecycleCallback, AbilityStage, application, UIAbility } from "@kit.AbilityKit";
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from "@kit.ArkUI";
import { BusinessError } from "@kit.BasicServicesKit";

const DOMAIN = 0x0000;
const TAG = 'testTag';

function loadContent() {
  // 加载数据
}

function releaseContent() {
  // 释放数据
}

function recordAbilityEvent(abilityName: string) {
  // 执行打点
}

function publishEvent() {
  // 对外发布通知
}

class MyAbilityLifecycleCallback extends AbilityLifecycleCallback {
  onAbilityCreate(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'onAbilityCreate: ' + ability.context.abilityInfo.name);
    // UIAbility事件打点记录
    recordAbilityEvent(ability.context.abilityInfo.name);
    // 模拟入口UIAbility创建时，加载资源对外发布通知
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      loadContent();
      publishEvent();
    }
  }

  onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageCreate.');
  }

  onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageActive.');
  }

  onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageInactive.');
  }

  onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageDestroy.');
  }

  onAbilityDestroy(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'onAbilityDestroy: ' + ability.context.abilityInfo.name);
    recordAbilityEvent(ability.context.abilityInfo.name);
    // 模拟入口UIAbility销毁时，释放资源
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      releaseContent();
      publishEvent();
    }
  }

  onAbilityForeground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityForeground.');
    recordAbilityEvent(ability.context.abilityInfo.name);
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      publishEvent();
    }
  }

  onAbilityBackground(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityBackground.');
    recordAbilityEvent(ability.context.abilityInfo.name);
    if (ability.context.abilityInfo.name === 'EntryAbility') {
      publishEvent();
    }
  }

  onAbilityContinue(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityContinue.');
  }

  onNewWantFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onNewWant');
  }

  onWillNewWantFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWillNewWant');
  }

  onAbilityWillCreateFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillCreate');
  }

  onWindowStageWillCreateFn(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillCreate');
  }

  onWindowStageWillDestroyFn(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillDestroy');
  }

  onAbilityWillDestroyFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillDestroy');
  }

  onAbilityWillForegroundFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillForeground');
  }

  onAbilityWillBackgroundFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillBackground');
  }

  onAbilityWillContinue(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillContinue.');
  }

  onWindowStageWillRestoreFn(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageWillRestore.');
  }

  onWindowStageRestoreFn(ability: UIAbility, windowStage: window.WindowStage) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onWindowStageRestore.');
  }

  onAbilityWillSaveStateFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilityWillSaveState.');
  }

  onAbilitySaveStateFn(ability: UIAbility) {
    hilog.info(DOMAIN, TAG, 'AbilityLifecycleCallback onAbilitySaveState.');
  }
}

let lifecycleId = -1; // 保存监听id

export default class MyStage extends AbilityStage {
  onCreate(): void {
    hilog.info(DOMAIN, TAG, 'AbilityStage onCreate')

    // AbilityStage创建时注册UIAbility生命周期监听，并把监听id保存起来
    try {
      let abilityLifecycleCallback = new MyAbilityLifecycleCallback();
      let applicationContext = application.getApplicationContextInstance();
      lifecycleId = applicationContext.onAbilityLifecycle(abilityLifecycleCallback);
    } catch (e) {
      hilog.error(DOMAIN, TAG, `register abilityLifecycle failed: ${JSON.stringify(e)}`);
    }
  }

  onDestroy(): void {
    // AbilityStage销毁时取消UIAbility生命周期监听注册
    let applicationContext = application.getApplicationContextInstance();
    applicationContext.offAbilityLifecycle(lifecycleId).catch((err) => {
      let e = err as BusinessError;
      hilog.error(DOMAIN, TAG, `unregister abilityLifecycle failed: ${JSON.stringify(e)}`);
    });
  }
}
```

```ts
// 以EntryAbility.ets为例，展示应用入口UIAbility
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';
import { BusinessError } from "@kit.BasicServicesKit";

const DOMAIN = 0x0000;
const TAG = 'testTag';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    this.context.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET);
    hilog.info(DOMAIN, TAG, 'EntryAbility onCreate');
  }

  onDestroy(): Promise<void> | undefined {
    hilog.info(DOMAIN, TAG, 'EntryAbility onDestroy');
    return undefined;
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // 主窗创建
    hilog.info(DOMAIN, TAG, 'EntryAbility onWindowStageCreate');

    windowStage.loadContent('pages/Index', (error): void => {
      let err = error as BusinessError;
      if (err.code) {
        hilog.error(DOMAIN, TAG, 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
        return;
      }
      hilog.info(DOMAIN, TAG, 'Succeeded in loading the content.');
    });
  }

  onWindowStageDestroy(): void {
    // 主窗销毁
    hilog.info(DOMAIN, TAG, 'EntryAbility onWindowStageDestroy');
  }

  onForeground(): void {
    // UIAbility切换到前台
    hilog.info(DOMAIN, TAG, 'EntryAbility onForeground');
  }

  onBackground(): void {
    // UIAbility切换到后台
    hilog.info(DOMAIN, TAG, 'EntryAbility  onBackground');
  }
}
```