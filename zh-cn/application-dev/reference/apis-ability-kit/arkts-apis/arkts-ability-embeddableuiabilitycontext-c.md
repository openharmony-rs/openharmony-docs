# EmbeddableUIAbilityContext

EmbeddableUIAbilityContext是
[EmbeddableUIAbility](arkts-ability-embeddableuiability-c.md#EmbeddableUIAbility)组件的上下文，继承自
[UIAbilityContext](arkts-ability-uiabilitycontext-c.md#UIAbilityContext)。

每个EmbeddableUIAbility组件实例化时，系统都会自动创建对应的EmbeddableUIAbilityContext。

> **说明：**
>
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** EmbeddableUIAbilityContext extends [UIAbilityContext](arkts-ability-uiabilitycontext-c.md#UIAbilityContext)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

