# getPartitionTable（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getPartitionTable

```TypeScript
function getPartitionTable(diskId: string): Promise<PartitionTableInfo>
```

根据磁盘ID获取分区表信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_FORMAT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function getPartitionTable(diskId: string): Promise<PartitionTableInfo>--><!--Device-volumeManager-function getPartitionTable(diskId: string): Promise<PartitionTableInfo>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| diskId | string | 是 | 磁盘ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PartitionTableInfo](arkts-corefile-volumemanager-partitiontableinfo-i-sys.md)&gt; | Promise对象，返回当前磁盘ID对应的分区表信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600021 | Get partition table failed. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// diskId可通过getAllDisks()接口获取
let diskId: string = "";
volumeManager.getPartitionTable(diskId).then((partitionTableInfo: volumeManager.PartitionTableInfo) => {
  console.info("getPartitionTable successfully:" + JSON.stringify(partitionTableInfo));
}).catch((error: BusinessError) => {
  console.error(`getPartitionTable failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

<!--DelEnd-->
