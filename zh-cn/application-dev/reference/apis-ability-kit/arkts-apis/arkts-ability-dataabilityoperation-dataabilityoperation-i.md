# DataAbilityOperation

定义DataAbility数据操作方式，可以作为[executeBatch](../../../reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md#dataabilityhelperexecutebatch)的入参，操作数据库的信息。

**起始版本：** 7

<!--Device-unnamed-export interface DataAbilityOperation--><!--Device-unnamed-export interface DataAbilityOperation-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## expectedCount

```TypeScript
expectedCount?: number
```

指示要更新或删除的预期行数。

**类型：** number

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-expectedCount?: number--><!--Device-DataAbilityOperation-expectedCount?: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## interrupted

```TypeScript
interrupted?: boolean
```

指示是否可以中断批处理操作。true表示可以中断批处理操作，false表示不可中断批处理操作。

**类型：** boolean

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-interrupted?: boolean--><!--Device-DataAbilityOperation-interrupted?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## predicates

```TypeScript
predicates?: dataAbility.DataAbilityPredicates
```

指示要设置的筛选条件。如果此参数为空，则操作所有数据记录。

**类型：** dataAbility.DataAbilityPredicates

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-predicates?: dataAbility.DataAbilityPredicates--><!--Device-DataAbilityOperation-predicates?: dataAbility.DataAbilityPredicates-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## predicatesBackReferences

```TypeScript
predicatesBackReferences?: Map<number, number>
```

指示用作谓词中筛选条件的反向引用。

**类型：** Map&lt;number, number&gt;

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-predicatesBackReferences?: Map<number, number>--><!--Device-DataAbilityOperation-predicatesBackReferences?: Map<number, number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## type

```TypeScript
type: featureAbility.DataAbilityOperationType
```

指示数据操作类型。

**类型：** featureAbility.DataAbilityOperationType

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-type: featureAbility.DataAbilityOperationType--><!--Device-DataAbilityOperation-type: featureAbility.DataAbilityOperationType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## uri

```TypeScript
uri: string
```

指示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。

**类型：** string

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-uri: string--><!--Device-DataAbilityOperation-uri: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## valueBackReferences

```TypeScript
valueBackReferences?: rdb.ValuesBucket
```

指示包含一组键值对的valuesBucket对象。

**类型：** rdb.ValuesBucket

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-valueBackReferences?: rdb.ValuesBucket--><!--Device-DataAbilityOperation-valueBackReferences?: rdb.ValuesBucket-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## valuesBucket

```TypeScript
valuesBucket?: rdb.ValuesBucket
```

指示要操作的数据值。

**类型：** rdb.ValuesBucket

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityOperation-valuesBucket?: rdb.ValuesBucket--><!--Device-DataAbilityOperation-valuesBucket?: rdb.ValuesBucket-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

