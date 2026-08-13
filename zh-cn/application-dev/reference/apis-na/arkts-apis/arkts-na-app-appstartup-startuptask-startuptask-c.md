# StartupTask

The module provides capabilities related to startup tasks in [AppStartup](../../../application-models/app-startup.md).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare class StartupTask--><!--Device-unnamed-declare class StartupTask-End-->

**系统能力：** SystemCapability.Ability.AppStartup

## init

```TypeScript
init(context: AbilityStageContext): Promise<Any> | Promise<void>
```

启动任务执行的初始化业务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupTask-init(context: AbilityStageContext): Promise<Any> | Promise<void>--><!--Device-StartupTask-init(context: AbilityStageContext): Promise<Any> | Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AbilityStageContext](../../apis-ability-kit/arkts-apis/arkts-ability-abilitystagecontext-c.md) | 是 | AbilityStage的上下文环境。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Any&gt; | Promise对象，返回启动任务执行结果对象。 |

## onDependencyCompleted

```TypeScript
onDependencyCompleted(dependency: string, result: Any): void
```

当依赖的启动任务执行完成时该方法将会被调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StartupTask-onDependencyCompleted(dependency: string, result: Any): void--><!--Device-StartupTask-onDependencyCompleted(dependency: string, result: Any): void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dependency | string | 是 | 依赖的启动任务名称。 |
| result | Any | 是 | 依赖启动任务执行的结果。 |

