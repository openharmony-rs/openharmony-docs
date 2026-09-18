# dump

## Modules to Import

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## dump

```TypeScript
function dump(filePath: string): Array<string>
```

Dumps the list of leaked objects and VM memory snapshot.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiChecker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path for storing exported information files.<br>**Note:**  Since API version 24, only the latest snapshot information is retained within the process lifecycle. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Export result. The file name extension is **.jsleaklist** for the list of leaked objects and **.heapsnapshot** for the VM memory snapshot.<br>Note: If the dump is successful, the path of the leaked object list file and the VM memory snapshot path are returned. Otherwise, an empty array is returned. |

**Examples**

```TypeScript
let context = this.getUIContext().getHostContext();
let files: Array<string> = jsLeakWatcher.dump(context?.filesDir);
```
