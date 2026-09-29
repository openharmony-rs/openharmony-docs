# AbilityResult

```TypeScript
export interface AbilityResult
```

The module defines the result code and data returned to the caller when a started UIAbility is terminated.

**Since:** 7

<!--Device-unnamed-export interface AbilityResult--><!--Device-unnamed-export interface AbilityResult-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## resultCode

```TypeScript
resultCode: number
```

Indicates the result code returned after the ability is destroyed. You can define the result code to identify an error.

**Type:** number

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityResult-resultCode: int--><!--Device-AbilityResult-resultCode: int-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## want

```TypeScript
want?: Want
```

Indicates the data returned after the ability is destroyed. You can define the data returned. This parameter can be null.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityResult-want?: Want--><!--Device-AbilityResult-want?: Want-End-->

**System capability:** SystemCapability.Ability.AbilityBase
