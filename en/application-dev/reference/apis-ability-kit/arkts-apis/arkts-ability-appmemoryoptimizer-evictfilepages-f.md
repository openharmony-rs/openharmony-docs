# evictFilePages

## Modules to Import

```TypeScript
import { appMemoryOptimizer } from '@kit.AbilityKit';
```

## evictFilePages

```TypeScript
function evictFilePages(fileNames: Array<string>): Promise<void>
```

Sends a request to the system to release file page cache of specified files. The system determines whether to actually perform the release based on the current memory status, and success is not guaranteed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fileNames | Array&lt;string&gt; | Yes | Array of file names for which file page cache needs to be released. File names must end with .so,hap, or .hsp. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000163](../errorcode-ability.md#16000163-file-type-error) | File type error. File name does not end with .so,hap, or .hsp. |
