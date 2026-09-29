# AbilityLifecycleState

```TypeScript
export enum AbilityLifecycleState
```

Enumerates the ability lifecycle states. It can be used in [getAbilityState(ability)](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md#getabilitystate) of [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) to return different ability lifecycle states.

**Since:** 9

<!--Device-abilityDelegatorRegistry-export enum AbilityLifecycleState--><!--Device-abilityDelegatorRegistry-export enum AbilityLifecycleState-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## UNINITIALIZED

```TypeScript
UNINITIALIZED = 0
```

The ability is in an invalid state.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityLifecycleState-UNINITIALIZED = 0--><!--Device-AbilityLifecycleState-UNINITIALIZED = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## CREATE

```TypeScript
CREATE = 1
```

The ability is created.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityLifecycleState-CREATE = 1--><!--Device-AbilityLifecycleState-CREATE = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## FOREGROUND

```TypeScript
FOREGROUND = 2
```

The ability is running in the foreground.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityLifecycleState-FOREGROUND = 2--><!--Device-AbilityLifecycleState-FOREGROUND = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## BACKGROUND

```TypeScript
BACKGROUND = 3
```

The ability is running in the background.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityLifecycleState-BACKGROUND = 3--><!--Device-AbilityLifecycleState-BACKGROUND = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## DESTROY

```TypeScript
DESTROY = 4
```

The ability is destroyed.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityLifecycleState-DESTROY = 4--><!--Device-AbilityLifecycleState-DESTROY = 4-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
