# LaunchReason

Ability启动原因，该类型为枚举，可配合UIAbility的[onCreate(want, launchParam)](arkts-ability-app-ability-uiability-uiability-c.md#oncreate-1)方法根据launchParam.launchReason的不同类型执行相应操作。

**起始版本：** 9

<!--Device-AbilityConstant-export enum LaunchReason--><!--Device-AbilityConstant-export enum LaunchReason-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知原因。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-UNKNOWN = 0--><!--Device-LaunchReason-UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## START_ABILITY

```TypeScript
START_ABILITY = 1
```

通过[startAbility](arkts-ability-uiabilitycontext-c.md#startability-1)接口启动Ability。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-START_ABILITY = 1--><!--Device-LaunchReason-START_ABILITY = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CALL

```TypeScript
CALL = 2
```

通过[startAbilityByCall](arkts-ability-uiabilitycontext-c.md#startabilitybycall-1)接口启动Ability。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-CALL = 2--><!--Device-LaunchReason-CALL = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION

```TypeScript
CONTINUATION = 3
```

跨端迁移启动Ability。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-CONTINUATION = 3--><!--Device-LaunchReason-CONTINUATION = 3-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## APP_RECOVERY

```TypeScript
APP_RECOVERY = 4
```

设置应用恢复后，应用故障时自动恢复启动Ability。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-APP_RECOVERY = 4--><!--Device-LaunchReason-APP_RECOVERY = 4-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## SHARE

```TypeScript
SHARE = 5
```

通过原子化服务分享启动Ability。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-SHARE = 5--><!--Device-LaunchReason-SHARE = 5-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## AUTO_STARTUP

```TypeScript
AUTO_STARTUP = 8
```

通过设置开机自启动来启动Ability。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchReason-AUTO_STARTUP = 8--><!--Device-LaunchReason-AUTO_STARTUP = 8-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## INSIGHT_INTENT

```TypeScript
INSIGHT_INTENT = 9
```

通过洞察意图来启动Ability。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-INSIGHT_INTENT = 9--><!--Device-LaunchReason-INSIGHT_INTENT = 9-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## PREPARE_CONTINUATION

```TypeScript
PREPARE_CONTINUATION = 10
```

跨端迁移提前启动Ability。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-PREPARE_CONTINUATION = 10--><!--Device-LaunchReason-PREPARE_CONTINUATION = 10-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## PRELOAD

```TypeScript
PRELOAD = 11
```

表明该UIAbility是通过预加载机制启动的。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LaunchReason-PRELOAD = 11--><!--Device-LaunchReason-PRELOAD = 11-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

