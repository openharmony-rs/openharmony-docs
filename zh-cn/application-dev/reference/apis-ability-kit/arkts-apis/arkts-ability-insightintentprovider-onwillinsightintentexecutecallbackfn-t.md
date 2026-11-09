# OnWillInsightIntentExecuteCallBackFn

```TypeScript
type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void
```

定义onWillInsightIntentExecuteCallBackFn函数。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-insightIntentProvider-type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void--><!--Device-insightIntentProvider-type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| executionInfo | [insightIntent.InsightIntentExecutionInfo](arkts-ability-insightintent-insightintentexecutioninfo-i.md) | 是 | 意图执行信息。 |
