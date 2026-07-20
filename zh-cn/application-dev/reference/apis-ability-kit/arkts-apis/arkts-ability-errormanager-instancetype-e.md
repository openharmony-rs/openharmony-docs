# InstanceType

虚拟机的实例类型。

**起始版本：** 18

<!--Device-errorManager-export enum InstanceType--><!--Device-errorManager-export enum InstanceType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## TASKPOOL

```TypeScript
TASKPOOL = 2
```

表示任务池虚拟机实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InstanceType-TASKPOOL = 2--><!--Device-InstanceType-TASKPOOL = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## WORKER

```TypeScript
WORKER = 1
```

表示工作虚拟机实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InstanceType-WORKER = 1--><!--Device-InstanceType-WORKER = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## MAIN

```TypeScript
MAIN = 0
```

表示主虚拟机实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InstanceType-MAIN = 0--><!--Device-InstanceType-MAIN = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## CUSTOM

```TypeScript
CUSTOM = 3
```

表示用户通过[napi_create_ark_runtime](docroot://reference/native-lib/napi.md#napi_create_ark_runtime)从本机代码创建的虚拟机实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-InstanceType-CUSTOM = 3--><!--Device-InstanceType-CUSTOM = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

