# AbilityResult

The module defines the result code and data returned to the caller when a started UIAbility is terminated.

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityBase

## resultCode

```TypeScript
resultCode: number
```

Indicates the result code returned after the ability is destroyed. You can define the result code to identify an error.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase

## want

```TypeScript
want?: Want
```

Indicates the data returned after the ability is destroyed. You can define the data returned. This parameter can be null.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityBase
