# onWillInsightIntentExecute

## Modules to Import

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## onWillInsightIntentExecute

```TypeScript
function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void
```

Registers a listener for insight intent execute.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-insightIntentProvider-function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void--><!--Device-insightIntentProvider-function onWillInsightIntentExecute(callback: InsightIntentExecutionCallBack): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [InsightIntentExecutionCallBack](arkts-ability-insightintentprovider-insightintentexecutioncallback-i.md) | Yes | The insight intent execution callback. |
