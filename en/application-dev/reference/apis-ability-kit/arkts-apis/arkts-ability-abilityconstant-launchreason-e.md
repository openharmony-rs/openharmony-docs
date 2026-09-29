# LaunchReason

```TypeScript
export enum LaunchReason
```

Enumerates the ability launch reasons. You can use it together with the value of **launchParam.launchReason** in [onCreate(want, launchParam)](arkts-ability-app-ability-uiability-uiability-c.md#oncreate) of the UIAbility to complete different operations.

**Since:** 9

<!--Device-AbilityConstant-export enum LaunchReason--><!--Device-AbilityConstant-export enum LaunchReason-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown reason.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-UNKNOWN = 0--><!--Device-LaunchReason-UNKNOWN = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## START_ABILITY

```TypeScript
START_ABILITY = 1
```

The ability is started by calling [startAbility](arkts-ability-uiabilitycontext-c.md#startability).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-START_ABILITY = 1--><!--Device-LaunchReason-START_ABILITY = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CALL

```TypeScript
CALL = 2
```

The ability is started by calling [startAbilityByCall](arkts-ability-uiabilitycontext-c.md#startabilitybycall).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-CALL = 2--><!--Device-LaunchReason-CALL = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CONTINUATION

```TypeScript
CONTINUATION = 3
```

The ability is started by means of cross-device migration.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-CONTINUATION = 3--><!--Device-LaunchReason-CONTINUATION = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## APP_RECOVERY

```TypeScript
APP_RECOVERY = 4
```

The ability is automatically started when the application is restored from a fault.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-APP_RECOVERY = 4--><!--Device-LaunchReason-APP_RECOVERY = 4-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## SHARE

```TypeScript
SHARE = 5
```

The ability is started by means of atomic service sharing.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-SHARE = 5--><!--Device-LaunchReason-SHARE = 5-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## AUTO_STARTUP

```TypeScript
AUTO_STARTUP = 8
```

The ability is automatically started upon system boot.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchReason-AUTO_STARTUP = 8--><!--Device-LaunchReason-AUTO_STARTUP = 8-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## INSIGHT_INTENT

```TypeScript
INSIGHT_INTENT = 9
```

The ability is started by the InsightIntent framework..

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LaunchReason-INSIGHT_INTENT = 9--><!--Device-LaunchReason-INSIGHT_INTENT = 9-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## PREPARE_CONTINUATION

```TypeScript
PREPARE_CONTINUATION = 10
```

The ability is started in advance during cross-device migration.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-LaunchReason-PREPARE_CONTINUATION = 10--><!--Device-LaunchReason-PREPARE_CONTINUATION = 10-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## PRELOAD

```TypeScript
PRELOAD = 11
```

The ability is started through preloading.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-LaunchReason-PRELOAD = 11--><!--Device-LaunchReason-PRELOAD = 11-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
