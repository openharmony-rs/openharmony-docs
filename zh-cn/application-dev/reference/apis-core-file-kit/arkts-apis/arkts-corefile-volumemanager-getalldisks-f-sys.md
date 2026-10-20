# getAllDisks（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getAllDisks

```TypeScript
function getAllDisks(): Promise<Array<Disk>>
```

查询所有磁盘信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function getAllDisks(): Promise<Array<Disk>>--><!--Device-volumeManager-function getAllDisks(): Promise<Array<Disk>>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[Disk](arkts-corefile-volumemanager-disk-i-sys.md)&gt;&gt; | Promise对象，返回所有磁盘信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllDisks().then((disks: Array<volumeManager.Disk>) => {
  console.info("getAllDisks successfully:" + JSON.stringify(disks));
}).catch((error: BusinessError) => {
  console.error(`getAllDisks failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

<!--DelEnd-->
