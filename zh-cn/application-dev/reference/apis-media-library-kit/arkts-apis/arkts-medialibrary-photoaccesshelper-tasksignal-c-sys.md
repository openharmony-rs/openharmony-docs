# TaskSignal（系统接口）

用于中断复制操作的信号。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancel

```TypeScript
cancel(): void
```

取消复制操作。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:  1. No task can be canceled. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

let taskSignal = new photoAccessHelper.TaskSignal();

try {
  taskSignal.cancel();
  console.info('cancel batch operation success');
} catch (err) {
  console.error(`cancel batch operation failed with error: ${err.code}, ${err.message}`);
}
```
