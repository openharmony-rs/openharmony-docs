# getTotalSizeSync

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getTotalSizeSync

```TypeScript
function getTotalSizeSync(): number
```

同步获取内置存储的总空间大小（单位为Byte）。

**起始版本：** 15

<!--Device-storageStatistics-function getTotalSizeSync(): long--><!--Device-storageStatistics-function getTotalSizeSync(): long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回内置存储的总空间大小（单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  let totalSize = storageStatistics.getTotalSizeSync();
  console.info('getTotalSizeSync successfully:' + totalSize);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`getTotalSizeSync failed. Code: ${error.code}, message: ${error.message}`);
}
```
