# stopOptimizeSpace（系统接口）

## stopOptimizeSpace

```TypeScript
function stopOptimizeSpace(): void
```

ͬ������ֹͣͼ����ͼ��Դ�ռ��Ż�����startOptimizeSpace���ʹ�á�

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let para:cloudSync.OptimizeSpaceParam = {totalSize: 1073741824, agingDays: 30};
let callback = (data:cloudSync.OptimizeSpaceProgress) => {
  if (data.state == cloudSync.OptimizeState.FAILED) {
    console.info("optimize space failed");
  } else if (data.state == cloudSync.OptimizeState.RUNNING) {
    console.info("optimize space progress: " + data.progress);
  }
}
cloudSync.startOptimizeSpace(para, callback);
cloudSync.stopOptimizeSpace();   // 停止空间优化

```

