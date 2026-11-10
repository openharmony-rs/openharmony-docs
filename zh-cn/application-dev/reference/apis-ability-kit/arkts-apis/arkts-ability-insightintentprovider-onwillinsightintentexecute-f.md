# onWillInsightIntentExecute

## 导入模块

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## onWillInsightIntentExecute

```TypeScript
function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void
```

注册意图执行的监听器。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-insightIntentProvider-function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void--><!--Device-insightIntentProvider-function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [InsightIntentExecutionCallBack](arkts-ability-insightintentprovider-insightintentexecutioncallback-i.md) | 是 | 意图执行回调。 |
