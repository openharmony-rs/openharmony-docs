# getFreeSize

## getFreeSize

```TypeScript
function getFreeSize(): Promise<long>
```

获取内置存储的可用空间大小（单位为Byte），以Promise方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-storageStatistics-function getFreeSize(): Promise<long>--><!--Device-storageStatistics-function getFreeSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回内置存储的可用空间大小（单位为Byte）。 (Unit: Byte) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getFreeSize().then((freeSize: number) => {
  console.info('getFreeSize successfully:' + freeSize);
}).catch((err: BusinessError) => {
  console.error(`getFreeSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let totalSize: long = 0;
storageStatistics.getFreeSize().then((freeSize) => {
  console.info('getFreeSize successfully:' + freeSize);
}).catch((err: BusinessError): void => {
  console.error(`getFreeSize failed. Code: ${err.code}, message: ${err.message}`);
});
```

