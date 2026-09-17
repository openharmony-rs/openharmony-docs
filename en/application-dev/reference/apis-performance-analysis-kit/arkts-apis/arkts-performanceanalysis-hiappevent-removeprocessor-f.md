# removeProcessor

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## removeProcessor

```TypeScript
function removeProcessor(id: number): void
```

Removes the data processor of a reported event.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | ID of a data processor. The value must be greater than **0**. The value is obtained by calling [addProcessor](arkts-performanceanalysis-hiappevent-addprocessor-f.md) or [addProcessorFromConfig](arkts-performanceanalysis-hiappevent-addprocessorfromconfig-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let processor: hiAppEvent.Processor = {
    name: 'analytics_demo'
  };
  let id: number = hiAppEvent.addProcessor(processor);
  // Remove a specified data processor based on the ID returned after the data processor is added.
  hiAppEvent.removeProcessor(id);
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to removeProcessor event, code=${error.code}`);
}
```
