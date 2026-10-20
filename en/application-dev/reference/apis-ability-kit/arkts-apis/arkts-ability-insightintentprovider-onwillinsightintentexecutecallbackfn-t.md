# OnWillInsightIntentExecuteCallBackFn

```TypeScript
type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void
```

Defines an onWillInsightIntentExecuteCallBackFn function.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-insightIntentProvider-type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void--><!--Device-insightIntentProvider-type OnWillInsightIntentExecuteCallBackFn = (executionInfo: insightIntent.InsightIntentExecutionInfo) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| executionInfo | [insightIntent.InsightIntentExecutionInfo](arkts-ability-insightintent-insightintentexecutioninfo-i.md) | Yes | The insight intent execute information. |
