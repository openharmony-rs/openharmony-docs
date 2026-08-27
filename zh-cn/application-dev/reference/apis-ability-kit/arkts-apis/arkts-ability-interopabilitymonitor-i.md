# InteropAbilityMonitor

本模块提供监听指定[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)生命周期状态变化的能力。开发者可以将InteropAbilityMonitor作为abilityDelegator. addInteropAbilityMonitorSync 的入参来注册监听。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityBackground

```TypeScript
onAbilityBackground?: AbilityCallbackFn
```

UIAbility对象状态变成后台时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityCreate

```TypeScript
onAbilityCreate?: AbilityCallbackFn
```

UIAbility对象被创建时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityDestroy

```TypeScript
onAbilityDestroy?: AbilityCallbackFn
```

UIAbility对象被销毁前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityForeground

```TypeScript
onAbilityForeground?: AbilityCallbackFn
```

UIAbility对象状态变成前台时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageCreate

```TypeScript
onWindowStageCreate?: AbilityCallbackFn
```

当WindowStage实例被创建时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy?: AbilityCallbackFn
```

当WindowStage被销毁前，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: AbilityCallbackFn
```

当UIAbility跨端迁移时，目标端UIAbility恢复页面栈时，触发该回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

被监听的UIAbility对象名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName?: string
```

被监听的UIAbility对象所属模块名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
