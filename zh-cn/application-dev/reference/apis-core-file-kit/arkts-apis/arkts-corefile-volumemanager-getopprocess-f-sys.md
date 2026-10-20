# getOpProcess（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## getOpProcess

```TypeScript
function getOpProcess(volumeId: string): Promise<number>
```

获取卷设备的操作进度，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function getOpProcess(volumeId: string): Promise<int>--><!--Device-volumeManager-function getOpProcess(volumeId: string): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumeId | string | 是 | 卷设备id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回操作进度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600010 | The input parameter is invalid. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// volumeId可通过getAllVolumes()接口获取
let volumeId: string = "";
volumeManager.getOpProcess(volumeId).then((progress: number) => {
  console.info("getOpProcess successfully, progress:" + progress);
}).catch((error: BusinessError) => {
  console.error(`Failed to getOpProcess. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
