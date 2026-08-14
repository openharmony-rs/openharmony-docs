# getTotalSize

## getTotalSize

```TypeScript
function getTotalSize(): Promise<long>
```

获取内置存储的总空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-storageStatistics-function getTotalSize(): Promise<long>--><!--Device-storageStatistics-function getTotalSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回内置存储的总空间大小（单位为Byte）。 (Unit: Byte) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalSize().then((totalSize: number) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError) => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let totalSize: long = 0;
storageStatistics.getTotalSize().then((totalSize) => {
  console.info('getTotalSize successfully:' + totalSize);
}).catch((err: BusinessError): void => {
  console.error(`getTotalSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

