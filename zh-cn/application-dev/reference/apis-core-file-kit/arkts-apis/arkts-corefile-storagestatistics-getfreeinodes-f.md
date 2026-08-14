# getFreeInodes

## getFreeInodes

```TypeScript
function getFreeInodes(): Promise<long>
```

获取文件系统的inode资源剩余量，仅支持查询系统数据分区。使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getFreeInodes(): Promise<long>--><!--Device-storageStatistics-function getFreeInodes(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象，返回文件系统inode资源剩余量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13600016 | Failed to query the inode information of the data partition. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getFreeInodes().then((freeInodes: number) => {
  console.info('getFreeInodes successfully:' + freeInodes);
}).catch((err: BusinessError) => {
  console.error(`getFreeInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getFreeInodes().then((freeInodes: long) => {
  console.info('getFreeInodes successfully:' + freeInodes);
}).catch((err: BusinessError): void => {
  console.error(`getFreeInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

