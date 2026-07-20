# DataAbilityResult

定义DataAbility数据操作结果，通过[executeBatch](docroot://reference/apis-ability-kit/js-apis-inner-ability-dataAbilityHelper.md#dataabilityhelperexecutebatch)操作数据库时，操作结果使用DataAbilityResult对象返回。

**起始版本：** 7

<!--Device-unnamed-export interface DataAbilityResult--><!--Device-unnamed-export interface DataAbilityResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## count

```TypeScript
count?: number
```

指示受操作影响的数据数量。

**类型：** number

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityResult-count?: number--><!--Device-DataAbilityResult-count?: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## uri

```TypeScript
uri?: string
```

指示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。

**类型：** string

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityResult-uri?: string--><!--Device-DataAbilityResult-uri?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

