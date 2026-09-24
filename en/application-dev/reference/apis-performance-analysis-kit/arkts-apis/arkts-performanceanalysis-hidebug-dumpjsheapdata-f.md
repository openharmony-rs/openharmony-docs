# dumpJsHeapData

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename : string) : void
```

Dumps VM heap data.

> **NOTE:** 
> 
> Exporting the VM heap is time-consuming, and this API is a synchronous API. Therefore, you are advised not to
> call this API in the release version. Otherwise, the application screen may freeze, affecting user experience.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filename | string | Yes | User-defined name of the VM heap data output file. The .heapsnapshot file is generated in the **files** directory of the application based on the specified file name. The maximum length of a string is 128 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | the parameter check failed, Parameter type error |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData");
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```


<a id="dumpjsheapdata-1"></a>

## dumpJsHeapData

```TypeScript
function dumpJsHeapData(filename : string, needClean : boolean) : void
```

Dumps VM heap data and clears the nodeId cache.

> **NOTE:** 
> 
> Exporting the VM heap is time-consuming, and this API is a synchronous API. Therefore, you are advised not to
> call this API in the release version. Otherwise, the application screen may freeze, affecting user experience.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filename | string | Yes | Custom name of the heap dump file. A **fileName.heapsnapshot** file will be generated in the **files** directory of the application. The maximum length of a string is 128 bytes. |
| needClean | boolean | Yes | Whether to clear the node ID cache before dumping heap snapshots. **true**: yes; **false**: no. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.dumpJsHeapData("heapData", true);
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```
