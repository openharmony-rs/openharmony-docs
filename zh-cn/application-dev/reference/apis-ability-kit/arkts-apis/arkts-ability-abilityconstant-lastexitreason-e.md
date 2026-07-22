# LastExitReason

Ability上次退出原因，该类型为枚举，可配合UIAbility的[onCreate()](arkts-ability-app-ability-uiability-uiability-c.md#oncreate)方法根据launchParam.lastExitReason的不同类型执行相应操作。

**起始版本：** 9

<!--Device-AbilityConstant-export enum LastExitReason--><!--Device-AbilityConstant-export enum LastExitReason-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知原因。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-UNKNOWN = 0--><!--Device-LastExitReason-UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ABILITY_NOT_RESPONDING

```TypeScript
ABILITY_NOT_RESPONDING = 1
```

Ability组件未响应。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [APP_FREEZE](arkts-ability-abilityconstant-lastexitreason-e.md#app_freeze)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LastExitReason-ABILITY_NOT_RESPONDING = 1--><!--Device-LastExitReason-ABILITY_NOT_RESPONDING = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NORMAL

```TypeScript
NORMAL = 2
```

用户主动关闭应用，应用程序正常退出。

**说明**：当开发者直接调用[process.exit()](../apis-arkts/js-apis-process.md#processexitdeprecated)、内核kill命令等非Ability Kit提供的能力强制退出应用进程时，也会返回NORMAL。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-NORMAL = 2--><!--Device-LastExitReason-NORMAL = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CPP_CRASH

```TypeScript
CPP_CRASH = 3
```

[进程崩溃](../../../dfx/cppcrash-guidelines.md)导致的应用程序退出。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-CPP_CRASH = 3--><!--Device-LastExitReason-CPP_CRASH = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## JS_ERROR

```TypeScript
JS_ERROR = 4
```

当应用存在JS语法错误并未被开发者捕获时，触发JS_ERROR故障，导致应用程序退出。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-JS_ERROR = 4--><!--Device-LastExitReason-JS_ERROR = 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## APP_FREEZE

```TypeScript
APP_FREEZE = 5
```

[应用冻屏](../../../dfx/appfreeze-guidelines.md)导致的应用程序退出。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-APP_FREEZE = 5--><!--Device-LastExitReason-APP_FREEZE = 5-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## PERFORMANCE_CONTROL

```TypeScript
PERFORMANCE_CONTROL = 6
```

因系统性能问题（如设备内存不足）导致的应用程序退出。

**说明**：该接口即将废弃，建议使用RESOURCE_CONTROL替代。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-PERFORMANCE_CONTROL = 6--><!--Device-LastExitReason-PERFORMANCE_CONTROL = 6-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## RESOURCE_CONTROL

```TypeScript
RESOURCE_CONTROL = 7
```

系统资源使用不当导致的应用程序退出。具体错误原因可以通过[LaunchParam.lastExitMessage](arkts-ability-abilityconstant-launchparam-i.md)获取，可能原因如下:

- CPU Highload，CPU高负载。  
- CPU_EXT Highload，快速CPU负载检测。  
- IO Manage Control，I/O管控。  
- App Memory Deterioration，应用内存超限劣化。  
- Temperature Control，温度管控。  
- Memory Pressure，整机低内存触发按优先级由低到高终止进程。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-RESOURCE_CONTROL = 7--><!--Device-LastExitReason-RESOURCE_CONTROL = 7-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UPGRADE

```TypeScript
UPGRADE = 8
```

应用升级导致的应用程序退出。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-UPGRADE = 8--><!--Device-LastExitReason-UPGRADE = 8-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## USER_REQUEST

```TypeScript
USER_REQUEST = 9
```

应用程序因多任务中心请求而退出。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-USER_REQUEST = 9--><!--Device-LastExitReason-USER_REQUEST = 9-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SIGNAL

```TypeScript
SIGNAL = 10
```

应用程序因收到系统kill指令信号而退出。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LastExitReason-SIGNAL = 10--><!--Device-LastExitReason-SIGNAL = 10-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

