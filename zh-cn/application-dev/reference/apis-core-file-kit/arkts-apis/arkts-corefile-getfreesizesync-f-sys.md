# getFreeSizeSync（系统接口）

## getFreeSizeSync

```TypeScript
function getFreeSizeSync(): number
```

同步获取内置存储的可用空间大小（单位为Byte）。

**起始版本：** 15

**需要权限：** 
- API版本10 - 14：ohos.permission.STORAGE_MANAGER

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回内置存储的可用空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>**适用版本：** 10 - 14 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.<br>**适用版本：** 10 - 14 |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let number = storageStatistics.getFreeSizeSync();
  console.info("getFreeSizeSync successfully:" + JSON.stringify(number));
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFreeSizeSync failed with error:" + JSON.stringify(error));
}

```

