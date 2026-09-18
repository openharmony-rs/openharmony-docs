# DataAbilityOperation

The module defines the operation on DataAbilities. It can be used as an input parameter of [executeBatch](../../../reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md#dataabilityhelperexecutebatch) to specify the database operation information.

**Since:** 7

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## expectedCount

```TypeScript
expectedCount?: number
```

Indicates the expected number of rows to update or delete.

**Type:** number

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## interrupted

```TypeScript
interrupted?: boolean
```

Specifies whether a batch operation can be interrupted.

**Type:** boolean

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## predicates

```TypeScript
predicates?: dataAbility.DataAbilityPredicates
```

Indicates the filter criteria to set. If this parameter is null, all data records will be operated by default.

**Type:** [dataAbility.DataAbilityPredicates](../../apis-arkdata/arkts-apis/arkts-arkdata-dataability-dataabilitypredicates-c.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## predicatesBackReferences

```TypeScript
predicatesBackReferences?: Map<number, number>
```

Indicates the back reference to be used as a filter criterion in predicates.

**Type:** Map&lt;number, number&gt;

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## type

```TypeScript
type: featureAbility.DataAbilityOperationType
```

Indicates a operation type.

**Type:** [featureAbility.DataAbilityOperationType](arkts-ability-featureability-dataabilityoperationtype-e.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## uri

```TypeScript
uri: string
```

Indicates the path of data to operate.

**Type:** string

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## valueBackReferences

```TypeScript
valueBackReferences?: rdb.ValuesBucket
```

Indicates the valuesBucket object containing a set of key-value pairs.

**Type:** [rdb.ValuesBucket](../../apis-arkdata/arkts-apis/arkts-arkdata-rdb-valuesbucket-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## valuesBucket

```TypeScript
valuesBucket?: rdb.ValuesBucket
```

Indicates the data values to be set.

**Type:** [rdb.ValuesBucket](../../apis-arkdata/arkts-apis/arkts-arkdata-rdb-valuesbucket-t.md)

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel
