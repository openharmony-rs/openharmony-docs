# isVolumeInUse（系统接口）

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## isVolumeInUse

```TypeScript
function isVolumeInUse(volumePath: string): Promise<boolean>
```

查询指定卷设备是否正在使用，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-volumeManager-function isVolumeInUse(volumePath: string): Promise<boolean>--><!--Device-volumeManager-function isVolumeInUse(volumePath: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volumePath | string | 是 | 卷设备路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回指定卷设备是否正在使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600010 | The input parameter is invalid. |
| 13600033 | Failed to query whether the specified volume is currently in use. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let volumePath: string = "";
volumeManager.isVolumeInUse(volumePath).then(() => {
  console.info("isVolumeInUse successfully.");
}).catch((error: BusinessError) => {
  console.error(`isVolumeInUse failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

<!--DelEnd-->
