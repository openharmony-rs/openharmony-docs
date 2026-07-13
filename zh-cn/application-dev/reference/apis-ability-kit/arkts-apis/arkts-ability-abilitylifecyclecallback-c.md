# AbilityLifecycleCallback

[UIAbility](arkts-app-ability-uiability.md)从创建到销毁过程其生命周期是动态变化的。
AbilityLifecycleCallback模块提供监听[UIAbility](arkts-app-ability-uiability.md)生命周期变化的能力，
可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityBackground

```TypeScript
onAbilityBackground(ability: UIAbility): void
```

在UIAbility的[onBackground](arkts-ability-uiability-c.md#onbackground-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityContinue

```TypeScript
onAbilityContinue(ability: UIAbility): void
```

在UIAbility的[onContinue](arkts-ability-uiability-c.md#oncontinue-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityCreate

```TypeScript
onAbilityCreate(ability: UIAbility): void
```

在UIAbility的[onCreate](arkts-ability-uiability-c.md#oncreate-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityDestroy

```TypeScript
onAbilityDestroy(ability: UIAbility): void
```

在UIAbility的[onDestroy](arkts-ability-uiability-c.md#ondestroy-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityForeground

```TypeScript
onAbilityForeground(ability: UIAbility): void
```

在UIAbility的[onForeground](arkts-ability-uiability-c.md#onforeground-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilitySaveState

```TypeScript
onAbilitySaveState?(ability: UIAbility): void
```

在UIAbility的[onSaveState](arkts-ability-uiability-c.md#onsavestate-1)触发后回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?(ability: UIAbility): void
```

在UIAbility的[onBackground](arkts-ability-uiability-c.md#onbackground-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?(ability: UIAbility): void
```

在UIAbility的[onContinue](arkts-ability-uiability-c.md#oncontinue-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?(ability: UIAbility): void
```

在UIAbility的[onCreate](arkts-ability-uiability-c.md#oncreate-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?(ability: UIAbility): void
```

在UIAbility的[onDestroy](arkts-ability-uiability-c.md#ondestroy-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?(ability: UIAbility): void
```

在UIAbility的[onForeground](arkts-ability-uiability-c.md#onforeground-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?(ability: UIAbility): void
```

在UIAbility的[onSaveState](arkts-ability-uiability-c.md#onsavestate-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onNewWant

```TypeScript
onNewWant?(ability: UIAbility): void
```

在UIAbility的[onNewWant](arkts-ability-uiability-c.md#onnewwant-1)触发后回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWillNewWant

```TypeScript
onWillNewWant?(ability: UIAbility): void
```

在UIAbility的[onNewWant](arkts-ability-uiability-c.md#onnewwant-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageActive

```TypeScript
onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility主窗获焦时触发回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageCreate

```TypeScript
onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageCreate](arkts-ability-uiability-c.md#onwindowstagecreate-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageDestroy](arkts-ability-uiability-c.md#onwindowstagedestroy-1)触发后回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageInactive

```TypeScript
onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility主窗失焦时触发回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageRestore

```TypeScript
onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageRestore](arkts-ability-uiability-c.md#onwindowstagerestore-1)触发后回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageCreate](arkts-ability-uiability-c.md#onwindowstagecreate-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageDestroy](arkts-ability-uiability-c.md#onwindowstagedestroy-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageRestore](arkts-ability-uiability-c.md#onwindowstagerestore-1)触发前回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | UIAbility | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

