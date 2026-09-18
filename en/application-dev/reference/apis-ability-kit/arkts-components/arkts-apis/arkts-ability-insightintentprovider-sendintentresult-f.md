# sendIntentResult

## Modules to Import

```TypeScript
import { insightIntentProvider } from '@kit.AbilityKit';
```

## sendIntentResult

```TypeScript
function sendIntentResult(instanceId: number, result: insightIntent.IntentResult<T>): Promise<void>
```

Send intent result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceId | number | Yes | The insight intent instance ID. It is from InsightIntentEntryExecutor.context.instanceId. |
| result | [insightIntent.IntentResult](arkts-ability-insightintent-intentresult-i.md)&lt;T&gt; | Yes | The result of insight intent execution. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

**Examples**

```TypeScript
Below is an example of setting the return mode of the intent execution result to FUNCTION.
```

```TypeScript
Below is an example of proactively sending the intent execution result.
```
