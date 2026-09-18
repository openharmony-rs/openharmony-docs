# StartAbilityParameter

The module defines the parameters for starting an ability. The parameters can be used as input parameters in [startAbility](arkts-ability-featureability-startability-f.md) to start the specified ability.

**Since:** 6

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSetting

```TypeScript
abilityStartSetting?: { [key: string]: any }
```

Indicates the special start setting used in starting ability.

**Type:** { [key: string]: any }

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## abilityStartSettings

```TypeScript
abilityStartSettings?: Record<string, Object>
```

Indicates the special start setting used in starting ability. The ability of this property is same as abilityStartSetting. If both are set, this property will be used.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## want

```TypeScript
want: Want
```

Indicates the Want containing information about the target ability to start.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel
