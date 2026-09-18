# addProcessorFromConfig

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addProcessorFromConfig

```TypeScript
function addProcessorFromConfig(processorName: string, configName?: string): Promise<number>
```

Adds the configuration information of the data processor. The configuration file contains information such as the name of the event received by the data processor. This API uses a promise to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| processorName | string | Yes | Name of a data processor. It can contain only letters, digits, underscores (_), and dollar signs (&#36;). It cannot start with a digit and cannot exceed 256 characters. |
| configName | string | No | Name of the data processor configuration. The corresponding configuration can be loaded from the configuration file. The default value is **SDK_OCG**. It can contain only letters, digits, underscores (_), and dollar signs (&#36;). It cannot start with a digit and cannot exceed 256 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the unique ID of the added event data processor, which can be used to remove the data processor. If the adding fails, error code **11105001** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11105001](../errorcode-hiappevent.md#11105001-invalid-parameter-value) | Invalid parameter value. Possible causes: 1. Incorrect parameter length; 2. Incorrect parameter format. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addProcessorFromConfig("test_name").then((processorId) => {
  hilog.info(0x0000, 'hiAppEvent', `Succeeded in adding processor from config, processorId=${processorId}`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `Failed to add processor from config, code: ${err.code}, message: ${err.message}`);
});
```
