# InteractionText（系统接口）

```TypeScript
interface InteractionText extends InteractionUI
```

定义当意图执行完成时TEXT要显示为交互界面的信息，不支持分布式。

**继承/实现关系：** InteractionText extends [InteractionUI](arkts-ability-insightintent-interactionui-i-sys.md)

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## buttons

```TypeScript
buttons?: Array<string>
```

按钮列表。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## interactionUIType

```TypeScript
interactionUIType: 'TEXT'
```

交互界面的类型，固定为'TEXT'。

**类型：** 'TEXT'

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters: Record<string, Object>
```

传递给目标Text的参数。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
