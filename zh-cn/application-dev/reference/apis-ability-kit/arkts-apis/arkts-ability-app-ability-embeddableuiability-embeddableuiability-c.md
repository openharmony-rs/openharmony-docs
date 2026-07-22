# EmbeddableUIAbility

EmbeddableUIAbility组件是为原子化服务提供可嵌入式的UIAbility组件，继承自[UIAbility](arkts-app-ability-uiability.md)。开发者通过实现EmbeddableUIAbility，为其他应用提供跳出式启动和嵌入式启动原子化服务方式。各类Ability的继承关系详见[继承关系说明](../../../reference/apis-ability-kit/js-apis-app-ability-ability.md#ability的继承关系说明)。

**继承/实现关系：** EmbeddableUIAbility extends [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)

**起始版本：** 12

<!--Device-unnamed-export default class EmbeddableUIAbility extends UIAbility--><!--Device-unnamed-export default class EmbeddableUIAbility extends UIAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { EmbeddableUIAbility } from '@kit.AbilityKit';
```

## context

```TypeScript
context: EmbeddableUIAbilityContext
```

EmbeddableUIAbility组件的上下文。

**类型：** EmbeddableUIAbilityContext

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddableUIAbility-context: EmbeddableUIAbilityContext--><!--Device-EmbeddableUIAbility-context: EmbeddableUIAbilityContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

