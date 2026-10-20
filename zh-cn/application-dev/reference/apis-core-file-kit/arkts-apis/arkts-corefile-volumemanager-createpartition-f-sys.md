# createPartition（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## createPartition

```TypeScript
function createPartition(diskId: string, params: PartitionParams): Promise<void>
```

在磁盘上创建分区，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_FORMAT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function createPartition(diskId: string, params: PartitionParams): Promise<void>--><!--Device-volumeManager-function createPartition(diskId: string, params: PartitionParams): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| diskId | string | 是 | 磁盘ID。 |
| params | [PartitionParams](arkts-corefile-volumemanager-partitionparams-i-sys.md) | 是 | 分区创建参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600022 | Create partition failed. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// diskId可通过getAllDisks()接口获取
let diskId: string = "";
let params: volumeManager.PartitionParams = {
  partitionNum: 1,
  startSector: 2048,
  endSector: 1024000,
  typeCode: "ext4"
};
volumeManager.createPartition(diskId, params).then(() => {
  console.info("createPartition successfully.");
}).catch((error: BusinessError) => {
  console.error(`createPartition failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

<!--DelEnd-->
