# getDiskById（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getDiskById

```TypeScript
function getDiskById(diskId: string): Promise<Disk>
```

根据磁盘ID查询磁盘信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function getDiskById(diskId: string): Promise<Disk>--><!--Device-volumeManager-function getDiskById(diskId: string): Promise<Disk>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| diskId | string | 是 | 磁盘id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Disk](arkts-corefile-volumemanager-disk-i-sys.md)&gt; | Promise对象，返回当前磁盘ID对应的磁盘信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// diskId可通过getAllDisks()接口获取
let diskId: string = "";
volumeManager.getDiskById(diskId).then((disk: volumeManager.Disk) => {
  console.info("getDiskById successfully:" + JSON.stringify(disk));
}).catch((error: BusinessError) => {
  console.error(`getDiskById failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

<!--DelEnd-->
