# AbilityLifecycleCallback

[UIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_从创建到销毁过程其生命周期是动态变化的。 AbilityLifecycleCallback模块提供监听[UIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_生命周期变化的能力， 可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class AbilityLifecycleCallback--><!--Device-unnamed-declare class AbilityLifecycleCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityBackground

```TypeScript
onAbilityBackground(ability: UIAbility): void
```

在UIAbility的[onBackground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityBackground(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityBackground(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityContinue

```TypeScript
onAbilityContinue(ability: UIAbility): void
```

在UIAbility的[onContinue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityContinue(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityContinue(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityCreate

```TypeScript
onAbilityCreate(ability: UIAbility): void
```

在UIAbility的[onCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityCreate(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityCreate(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityDestroy

```TypeScript
onAbilityDestroy(ability: UIAbility): void
```

在UIAbility的[onDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityDestroy(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityDestroy(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityForeground

```TypeScript
onAbilityForeground(ability: UIAbility): void
```

在UIAbility的[onForeground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityForeground(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityForeground(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilitySaveState

```TypeScript
onAbilitySaveState?(ability: UIAbility): void
```

在UIAbility的[onSaveState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilitySaveState?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilitySaveState?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?(ability: UIAbility): void
```

在UIAbility的[onBackground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillBackground?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillBackground?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?(ability: UIAbility): void
```

在UIAbility的[onContinue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillContinue?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillContinue?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?(ability: UIAbility): void
```

在UIAbility的[onCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillCreate?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillCreate?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?(ability: UIAbility): void
```

在UIAbility的[onDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillDestroy?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillDestroy?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?(ability: UIAbility): void
```

在UIAbility的[onForeground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillForeground?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillForeground?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?(ability: UIAbility): void
```

在UIAbility的[onSaveState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillSaveState?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onAbilityWillSaveState?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onNewWant

```TypeScript
onNewWant?(ability: UIAbility): void
```

在UIAbility的[onNewWant]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onNewWant?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onNewWant?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWillNewWant

```TypeScript
onWillNewWant?(ability: UIAbility): void
```

在UIAbility的[onNewWant]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWillNewWant?(ability: UIAbility): void--><!--Device-AbilityLifecycleCallback-onWillNewWant?(ability: UIAbility): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageActive

```TypeScript
onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility主窗获焦时触发回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageCreate

```TypeScript
onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageInactive

```TypeScript
onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility主窗失焦时触发回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageRestore

```TypeScript
onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageRestore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

在UIAbility的[onWindowStageRestore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void--><!--Device-AbilityLifecycleCallback-onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调事件对应的UIAbility对象。 |
| windowStage | window.WindowStage | 是 | 回调事件对应的UIAbility主窗管理器。 |

**示例：**

参见[AbilityLifecycleCallback使用示例](#abilitylifecyclecallback使用示例)。

## onAbilitySaveState

```TypeScript
onAbilitySaveState?: OnAbilitySaveStateFn
```

在UIAbility的[onSaveState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**类型：** OnAbilitySaveStateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilitySaveState?: OnAbilitySaveStateFn--><!--Device-AbilityLifecycleCallback-onAbilitySaveState?: OnAbilitySaveStateFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?: OnAbilityWillBackgroundFn
```

在UIAbility的[onBackground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillBackgroundFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillBackground?: OnAbilityWillBackgroundFn--><!--Device-AbilityLifecycleCallback-onAbilityWillBackground?: OnAbilityWillBackgroundFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?: OnAbilityWillContinueFn
```

在UIAbility的[onContinue]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillContinueFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillContinue?: OnAbilityWillContinueFn--><!--Device-AbilityLifecycleCallback-onAbilityWillContinue?: OnAbilityWillContinueFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?: OnAbilityWillCreateFn
```

在UIAbility的[onCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillCreateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillCreate?: OnAbilityWillCreateFn--><!--Device-AbilityLifecycleCallback-onAbilityWillCreate?: OnAbilityWillCreateFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?: OnAbilityWillDestroyFn
```

在UIAbility的[onDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillDestroyFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillDestroy?: OnAbilityWillDestroyFn--><!--Device-AbilityLifecycleCallback-onAbilityWillDestroy?: OnAbilityWillDestroyFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?: OnAbilityWillForegroundFn
```

在UIAbility的[onForeground]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillForegroundFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillForeground?: OnAbilityWillForegroundFn--><!--Device-AbilityLifecycleCallback-onAbilityWillForeground?: OnAbilityWillForegroundFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?: OnAbilityWillSaveStateFn
```

在UIAbility的[onSaveState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnAbilityWillSaveStateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onAbilityWillSaveState?: OnAbilityWillSaveStateFn--><!--Device-AbilityLifecycleCallback-onAbilityWillSaveState?: OnAbilityWillSaveStateFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onNewWant

```TypeScript
onNewWant?: OnNewWantFn
```

在UIAbility的[onNewWant]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**类型：** OnNewWantFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onNewWant?: OnNewWantFn--><!--Device-AbilityLifecycleCallback-onNewWant?: OnNewWantFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWillNewWant

```TypeScript
onWillNewWant?: OnWillNewWantFn
```

在UIAbility的[onNewWant]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnWillNewWantFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onWillNewWant?: OnWillNewWantFn--><!--Device-AbilityLifecycleCallback-onWillNewWant?: OnWillNewWantFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: OnWindowStageRestoreFn
```

在UIAbility的[onWindowStageRestore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发后回调。

**类型：** OnWindowStageRestoreFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onWindowStageRestore?: OnWindowStageRestoreFn--><!--Device-AbilityLifecycleCallback-onWindowStageRestore?: OnWindowStageRestoreFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?: OnWindowStageWillCreateFn
```

在UIAbility的[onWindowStageCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnWindowStageWillCreateFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillCreate?: OnWindowStageWillCreateFn--><!--Device-AbilityLifecycleCallback-onWindowStageWillCreate?: OnWindowStageWillCreateFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?: OnWindowStageWillDestroyFn
```

在UIAbility的[onWindowStageDestroy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnWindowStageWillDestroyFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillDestroy?: OnWindowStageWillDestroyFn--><!--Device-AbilityLifecycleCallback-onWindowStageWillDestroy?: OnWindowStageWillDestroyFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?: OnWindowStageWillRestoreFn
```

在UIAbility的[onWindowStageRestore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发前回调。

**类型：** OnWindowStageWillRestoreFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AbilityLifecycleCallback-onWindowStageWillRestore?: OnWindowStageWillRestoreFn--><!--Device-AbilityLifecycleCallback-onWindowStageWillRestore?: OnWindowStageWillRestoreFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

