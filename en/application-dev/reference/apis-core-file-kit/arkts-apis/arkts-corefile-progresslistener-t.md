# ProgressListener

```TypeScript
type ProgressListener = (progress: Progress) => void
```

Defines the listener used to observe the copy progress.

**Since:** 11

<!--Device-unnamed-type ProgressListener = (progress: Progress) => void--><!--Device-unnamed-type ProgressListener = (progress: Progress) => void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | [Progress](arkts-corefile-file-fs-progress-i.md) | Yes | Listener used to observe the copy progress. |

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
