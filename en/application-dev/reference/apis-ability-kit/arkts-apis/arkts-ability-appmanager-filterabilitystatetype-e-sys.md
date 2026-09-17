# FilterAbilityStateType (System API)

Enumerates the types of ability states to filter. It can be used with [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) to filter the ability state types you want to listen for.

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## CREATE

```TypeScript
CREATE = 1 << 0
```

The ability is being created. It corresponds to the state **ABILITY_STATE_CREATE** in [Ability States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-states).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## FOREGROUND

```TypeScript
FOREGROUND = 1 << 1
```

The ability is running in the foreground. It corresponds to the state **ABILITY_STATE_FOREGROUND** in [Ability States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-states).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## BACKGROUND

```TypeScript
BACKGROUND = 1 << 2
```

The ability is running in the background. It corresponds to the state **ABILITY_STATE_BACKGROUND** in [Ability States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-states).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## DESTROY

```TypeScript
DESTROY = 1 << 3
```

The ability has been destroyed. It corresponds to the state **ABILITY_STATE_TERMINATED** in [Ability States](../../../reference/apis-ability-kit/js-apis-inner-application-abilityStateData.md#ability-states).

**Since:** 21

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
