# getFreeSizeSync

## getFreeSizeSync

```TypeScript
function getFreeSizeSync(): long
```

同步获取内置存储的可用空间大小（单位为Byte）。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本10 - 14：ohos.permission.STORAGE_MANAGER

<!--Device-storageStatistics-function getFreeSizeSync(): long--><!--Device-storageStatistics-function getFreeSizeSync(): long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 返回内置存储的可用空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 10 - 14 |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let freeSize = storageStatistics.getFreeSizeSync();
  console.info('getFreeSizeSync successfully:' + freeSize);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`getFreeSizeSync failed. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let freeSize = storageStatistics.getFreeSizeSync();
  console.info('getFreeSizeSync successfully:' + freeSize);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`getFreeSizeSync failed. Code: ${err.code}, message: ${err.message}`);
}
```

