# ProgressListener

```TypeScript
type ProgressListener = (progress: Progress) => void
```

Listener used to observe the copy progress.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | [Progress](arkts-corefile-file-fs-progress-i.md) | Yes | indicates the progress data of copyFile |

**Examples**

```TypeScript
import { TaskSignal } from '@kit.CoreFileKit';

let copySignal: fileIo.TaskSignal = new TaskSignal();
let progressListener: fileIo.ProgressListener = (progress: fileIo.Progress) => {
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
};
let copyOption: fileIo.CopyOptions = {
  "progressListener" : progressListener,
  "copySignal" : copySignal,
}
```
