# evictModuleFilePages

## Modules to Import

```TypeScript
import { appMemoryOptimizer } from '@kit.AbilityKit';
```

## evictModuleFilePages

```TypeScript
function evictModuleFilePages(moduleNames: Array<string>): Promise<void>
```

Sends a request to the system to release file page cache of specified modules. The system determines whether to actually perform the release based on the current memory status, and success is not guaranteed. The system reads the memory_optimizer.json configuration file of the corresponding module, obtains the evictFilePages array, and performs file page cache eviction on the files in the array.

Configuration file path: {Module directory}/src/main/resources/rawfile/memory_optimizer.json File names in the evictFilePages array of the configuration file must end with .so,hap, or .hsp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleNames | Array&lt;string&gt; | Yes | Array of module names for which file page cache needs to be released. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000163](../errorcode-ability.md#16000163-file-type-error) | File type error. File names in the evictFilePages array of the configuration file do not end with .so,hap, or .hsp. |
| [16000164](../errorcode-ability.md#16000164-failed-to-parse-the-configuration-file) | Failed to parse configuration file. |
