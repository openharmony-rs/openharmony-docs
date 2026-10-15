# InstanceType

```TypeScript
export enum InstanceType
```

Enumerates the VM instance types.

**Since:** 18

<!--Device-errorManager-export enum InstanceType--><!--Device-errorManager-export enum InstanceType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## CUSTOM

```TypeScript
CUSTOM = 3
```

VM instance created from the local code using [napi_create_ark_runtime](../../../reference/native-lib/napi.md#napi_create_ark_runtime).

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-InstanceType-CUSTOM = 3--><!--Device-InstanceType-CUSTOM = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## MAIN

```TypeScript
MAIN = 0
```

Main VM instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-InstanceType-MAIN = 0--><!--Device-InstanceType-MAIN = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## TASKPOOL

```TypeScript
TASKPOOL = 2
```

TaskPool VM instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-InstanceType-TASKPOOL = 2--><!--Device-InstanceType-TASKPOOL = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## WORKER

```TypeScript
WORKER = 1
```

Worker VM instance.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-InstanceType-WORKER = 1--><!--Device-InstanceType-WORKER = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
