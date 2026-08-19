# ApplicationStateChangeCallback

本模块用于监听当前应用进程的状态变化。为了便于表述，下文中将“应用进程”简称为“进程”。 开发者可调用 [ApplicationContext.on('applicationStateChange')](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#onabilitylifecycle) 方法传入自定义ApplicationStateChangeCallback来监听当前进程的前后台状态变化，从而根据进程前后台状态变化来执行某些操作。例如，统计进程前后台时长、或者当进程退到后台时清理内存缓存。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare interface ApplicationStateChangeCallback--><!--Device-unnamed-declare interface ApplicationStateChangeCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## 导入模块

```TypeScript
```

## onApplicationBackground

```TypeScript
onApplicationBackground(): void
```

当前进程从前台切换到后台时触发回调。当该回调触发时，表示进程已完全处于后台状态，可以执行适合在后台状态下完成的操作（例如清理内存缓存）。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationStateChangeCallback-onApplicationBackground(): void--><!--Device-ApplicationStateChangeCallback-onApplicationBackground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## onApplicationForeground

```TypeScript
onApplicationForeground(): void
```

当前进程从后台切换到前台时触发回调。当该回调触发时，并不表示进程已完全处于前台状态，而是即将进入前台状态，此时无法执行需要依赖前台状态的操作（例如启动其他UIAbility）。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationStateChangeCallback-onApplicationForeground(): void--><!--Device-ApplicationStateChangeCallback-onApplicationForeground(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

