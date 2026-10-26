# InsightIntentContext（系统接口）

```TypeScript
declare class InsightIntentContext
```

本模块提供意图执行上下文，是[意图执行基类](arkts-ability-app-ability-insightintentexecutor-insightintentexecutor-c.md)和[@InsightIntentEntry的意图执行基类](arkts-ability-app-ability-insightintententryexecutor-insightintententryexecutor-c.md)的属性，为意图执行提供基础能力，例如启动本应用内的[UIAbility组件](arkts-ability-app-ability-uiability-uiability-c.md)。

**起始版本：** 11

<!--Device-unnamed-declare class InsightIntentContext--><!--Device-unnamed-declare class InsightIntentContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { InsightIntentContext } from '@kit.AbilityKit';
```

## toolCallId

```TypeScript
readonly toolCallId?: string
```

调用方传入的工具调用ID，用于关联本次意图执行与测试步骤。当调用方未传入工具调用ID或传入空字符串时，该值为undefined。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InsightIntentContext-readonly toolCallId?: string--><!--Device-InsightIntentContext-readonly toolCallId?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
