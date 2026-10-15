# DataAbilityResult

```TypeScript
export interface DataAbilityResult
```

The module defines the operation result on DataAbilities. When you call [executeBatch](../../../reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md#dataabilityhelperexecutebatch) to operate the database, the operation result is returned through the DataAbilityResult object.

**Since:** 7

<!--Device-unnamed-export interface DataAbilityResult--><!--Device-unnamed-export interface DataAbilityResult-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## count

```TypeScript
count?: number
```

Indicates the number of rows affected by the operation.

**Type:** number

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-DataAbilityResult-count?: number--><!--Device-DataAbilityResult-count?: number-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## uri

```TypeScript
uri?: string
```

Indicates the path of data to operate.

**Type:** string

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-DataAbilityResult-uri?: string--><!--Device-DataAbilityResult-uri?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel
