# EmbeddableUIAbilityContext

EmbeddableUIAbilityContext是[EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md)组件的上下文，继承自[UIAbilityContext](arkts-ability-uiabilitycontext-c.md)。

每个EmbeddableUIAbility组件实例化时，系统都会自动创建对应的EmbeddableUIAbilityContext。
> **说明：**  
>  
> - 本模块接口需要在主线程中使用，不要在Worker、TaskPool等子线程中使用。

**继承/实现关系：** EmbeddableUIAbilityContext extends [UIAbilityContext](arkts-ability-uiabilitycontext-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export default class EmbeddableUIAbilityContext extends UIAbilityContext--><!--Device-unnamed-export default class EmbeddableUIAbilityContext extends UIAbilityContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

