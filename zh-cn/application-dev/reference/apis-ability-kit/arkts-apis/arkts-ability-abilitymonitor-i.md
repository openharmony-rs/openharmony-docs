# AbilityMonitor

本模块提供监听指定[UIAbility](arkts-app-ability-uiability.md)生命周期状态变化的能力。开发者可以将AbilityMonitor作为[abilityDelegator.addAbilityMonitor](arkts-ability-abilitydelegator-i.md#addabilitymonitor-1)的入参来注册监听。

**起始版本：** 9

<!--Device-unnamed-export interface AbilityMonitor--><!--Device-unnamed-export interface AbilityMonitor-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

被监听的UIAbility对象名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-abilityName: string--><!--Device-AbilityMonitor-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName?: string
```

被监听的UIAbility对象所属模块名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-moduleName?: string--><!--Device-AbilityMonitor-moduleName?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityBackground

```TypeScript
onAbilityBackground?: (ability: UIAbility) => void
```

UIAbility对象状态变成后台时，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onAbilityBackground?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityBackground?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityCreate

```TypeScript
onAbilityCreate?: (ability: UIAbility) => void
```

UIAbility对象被创建时，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onAbilityCreate?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityCreate?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityDestroy

```TypeScript
onAbilityDestroy?: (ability: UIAbility) => void
```

UIAbility对象被销毁前，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onAbilityDestroy?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityDestroy?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityForeground

```TypeScript
onAbilityForeground?: (ability: UIAbility) => void
```

UIAbility对象状态变成前台时，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onAbilityForeground?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityForeground?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageCreate

```TypeScript
onWindowStageCreate?: (ability: UIAbility) => void
```

当WindowStage实例被创建时，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onWindowStageCreate?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageCreate?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy?: (ability: UIAbility) => void
```

当WindowStage被销毁前，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onWindowStageDestroy?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageDestroy?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: (ability: UIAbility) => void
```

当UIAbility跨端迁移时，目标端UIAbility恢复页面栈时，触发该回调函数。

**类型：** (ability: UIAbility) => void

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityMonitor-onWindowStageRestore?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageRestore?: (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

