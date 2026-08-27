# ProgressListener

```TypeScript
type ProgressListener = (progress: Progress) => void
```

拷贝进度监听。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | [Progress](arkts-corefile-file-fs-progress-i.md) | 是 | 拷贝进度监听。 |

**示例**

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
