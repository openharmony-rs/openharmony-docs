# offWillInsightIntentExecute

## Modules to Import

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## offWillInsightIntentExecute

```TypeScript
function offWillInsightIntentExecute(callback?: InsightIntentExecutionCallBack): void
```

unregisters a listener for insight intent execute.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-insightIntentProvider-function offWillInsightIntentExecute(callback?: InsightIntentExecutionCallBack): void--><!--Device-insightIntentProvider-function offWillInsightIntentExecute(callback?: InsightIntentExecutionCallBack): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [InsightIntentExecutionCallBack](arkts-ability-insightintentprovider-insightintentexecutioncallback-i.md) | No | The insight intent execution callback. If a defined callback is passed in, the listener for that callback is unregistered. If no value is passed in, all the listeners for insight intent execute are unregistered. |
