# dumpJsRawHeapData

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## dumpJsRawHeapData

```TypeScript
function dumpJsRawHeapData(needGC?: boolean): Promise<string>
```

Dumps the original heap snapshot of the VM for the current thread and generates a .rawheap file. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing.

> **NOTE:** 
> 
> This API is resource-consuming. Therefore, the calling frequency and times are strictly limited. You need to
> delete the files immediately after processing them.
> 
> You are advised to enable **Developer options** before calling this API, so that the calling quota is not
> limited. The setting takes effect after the device is restarted.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| needGC | boolean | No | Whether GC is required before storing heap snapshots. The value **true** indicates that GC is required, and **false** indicates the opposite. The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Path of the generated snapshot file. (Application Sandbox) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400106](../errorcode-hiviewdfx-hidebug-trace.md#11400106-api-call-quota-exceeded) | Quota exceeded. |
| [11400107](../errorcode-hiviewdfx-hidebug.md#11400107-failed-to-fork-the-child-dump-process) | Fork operation failed. |
| [11400108](../errorcode-hiviewdfx-hidebug.md#11400108-failed-to-wait-for-the-child-dump-process-to-finish) | Failed to wait for the child process to finish. |
| [11400109](../errorcode-hiviewdfx-hidebug.md#11400109-waiting-for-the-child-dump-process-times-out) | Timeout while waiting for the child process to finish. |
| [11400110](../errorcode-hiviewdfx-hidebug.md#11400110-insufficient-disk-space) | Disk remaining space too low. |
| [11400111](../errorcode-hiviewdfx-hidebug.md#11400111-failed-to-call-the-node-api) | Napi interface call exception. |
| [11400112](../errorcode-hiviewdfx-hidebug.md#11400112-repeated-data-dump) | Repeated data dump. |
| [11400113](../errorcode-hiviewdfx-hidebug.md#11400113-failed-to-create-a-dump-file) | Failed to create dump file. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';
hidebug.dumpJsRawHeapData().then((filePath: string) => {
  console.info(`dumpJsRawHeapData success and generated file path is ${filePath}`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.dumpJsRawHeapData(true, true).then((filePath: string) => {
  console.info(`dumpJsRawHeapData success and generated file path is ${filePath}`);
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.dumpJsRawHeapData(true, true, true).then((filePathArray: Array<string>) => {
  console.info(`dumpJsRawHeapData success and generated file path is ${JSON.stringify(filePathArray)}`);
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}`);
})
```


## dumpJsRawHeapData

```TypeScript
function dumpJsRawHeapData(needGC: boolean, needClean: boolean): Promise<string>
```

Dumps the original heap snapshot of the VM for the current thread and clears the **nodeId** cache. The generated file is in the rawheap format. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing.

> **NOTE:** 
> 
> This API is resource-consuming. Therefore, the calling frequency and times are strictly limited. You need to
> delete the files immediately after processing them.
> 
> You are advised to enable **Developer options** before calling this API, so that the calling quota is not
> limited. The setting takes effect after the device is restarted.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| needGC | boolean | Yes | Whether GC is required before storing heap snapshots. **true**: yes; **false**: no. |
| needClean | boolean | Yes | Whether to clear the node ID before dumping heap snapshots. **true**: yes; **false**: no. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Path of the generated snapshot file. (Application Sandbox) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400106](../errorcode-hiviewdfx-hidebug-trace.md#11400106-api-call-quota-exceeded) | Quota exceeded. |
| [11400107](../errorcode-hiviewdfx-hidebug.md#11400107-failed-to-fork-the-child-dump-process) | Fork operation failed. |
| [11400108](../errorcode-hiviewdfx-hidebug.md#11400108-failed-to-wait-for-the-child-dump-process-to-finish) | Failed to wait for the child process to finish. |
| [11400109](../errorcode-hiviewdfx-hidebug.md#11400109-waiting-for-the-child-dump-process-times-out) | Timeout while waiting for the child process to finish. |
| [11400110](../errorcode-hiviewdfx-hidebug.md#11400110-insufficient-disk-space) | Disk remaining space too low. |
| [11400111](../errorcode-hiviewdfx-hidebug.md#11400111-failed-to-call-the-node-api) | Napi interface call exception. |
| [11400112](../errorcode-hiviewdfx-hidebug.md#11400112-repeated-data-dump) | Repeated data dump. |
| [11400113](../errorcode-hiviewdfx-hidebug.md#11400113-failed-to-create-a-dump-file) | Failed to create dump file. |

**Examples**

See [dumpJsRawHeapData](#dumpjsrawheapdata)


## dumpJsRawHeapData

```TypeScript
function dumpJsRawHeapData(needGC: boolean, needClean: boolean, processDump: boolean): Promise<Array<string>>
```

Dumps the original heap snapshot of the VM for the current thread or the process to which the current thread belongs, clears the nodeId cache, and generates a .rawheap file. This API uses a promise to return the result. The file can be converted into a heapsnapshot file using rawheap-translator for parsing.

> **NOTE:** 
> 
> This API is resource-consuming. Therefore, the calling frequency and times are strictly limited. You need to
> delete the files immediately after processing them.
> 
> You are advised to enable **Developer options** before calling this API, so that the calling quota is not
> limited. The setting takes effect after the device is restarted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| needGC | boolean | Yes | Whether GC is required before storing heap snapshots. **true**: yes; **false**: no. |
| needClean | boolean | Yes | Whether to clear the node ID before dumping heap snapshots. **true**: yes; **false**: no. |
| processDump | boolean | Yes | Whether to dump the original heap snapshot of the process to which the current thread belongs. **true**: yes. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Array of paths of the generated snapshot files. (Application Sandbox) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400106](../errorcode-hiviewdfx-hidebug-trace.md#11400106-api-call-quota-exceeded) | Quota exceeded. |
| [11400107](../errorcode-hiviewdfx-hidebug.md#11400107-failed-to-fork-the-child-dump-process) | Fork operation failed. |
| [11400108](../errorcode-hiviewdfx-hidebug.md#11400108-failed-to-wait-for-the-child-dump-process-to-finish) | Failed to wait for the child process to finish. |
| [11400109](../errorcode-hiviewdfx-hidebug.md#11400109-waiting-for-the-child-dump-process-times-out) | Timeout while waiting for the child process to finish. |
| [11400110](../errorcode-hiviewdfx-hidebug.md#11400110-insufficient-disk-space) | Disk remaining space too low. |
| [11400111](../errorcode-hiviewdfx-hidebug.md#11400111-failed-to-call-the-node-api) | Napi interface call exception. |
| [11400112](../errorcode-hiviewdfx-hidebug.md#11400112-repeated-data-dump) | Repeated data dump. |
| [11400113](../errorcode-hiviewdfx-hidebug.md#11400113-failed-to-create-a-dump-file) | Failed to create dump file. |

**Examples**

See [dumpJsRawHeapData](#dumpjsrawheapdata)
