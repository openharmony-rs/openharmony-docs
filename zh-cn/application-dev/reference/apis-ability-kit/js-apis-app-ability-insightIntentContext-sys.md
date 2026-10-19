# @ohos.app.ability.InsightIntentContext (意图执行上下文)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供意图执行上下文，是[意图执行基类](js-apis-app-ability-insightIntentExecutor.md)和[@InsightIntentEntry的意图执行基类](js-apis-app-ability-InsightIntentEntryExecutor.md)的属性，为意图执行提供基础能力，例如启动本应用内的[UIAbility](js-apis-app-ability-uiAbility.md)组件。

**起始版本：** 26.2.0

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.InsightIntentContext (意图执行上下文)](js-apis-app-ability-insightIntentContext.md)。

## 导入模块

```ts
import { InsightIntentContext } from '@kit.AbilityKit';
```

## 属性

**起始版本：** 26.2.0

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**系统接口**：此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| toolCallId | string | 是 | 是 | 调用方传入的工具调用ID，用于将本次意图执行与调用方的维测步骤进行关联。当调用方未传入工具调用ID或传入空字符串时，该属性值为undefined。 |
