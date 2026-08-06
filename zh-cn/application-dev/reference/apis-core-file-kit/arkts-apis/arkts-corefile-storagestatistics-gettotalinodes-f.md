# getTotalInodes

## getTotalInodes

```TypeScript
function getTotalInodes(): Promise<long>
```

获取文件系统的inode资源总量，仅支持查询系统数据分区。使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getTotalInodes(): Promise<long>--><!--Device-storageStatistics-function getTotalInodes(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回文件系统inode资源总量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13600016 | Failed to query the inode information of the data partition. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalInodes().then((totalInodes: number) => {
  console.info('getTotalInodes successfully:' + totalInodes);
}).catch((err: BusinessError) => {
  console.error(`getTotalInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getTotalInodes().then((totalInodes: long) => {
  console.info('getTotalInodes successfully:' + totalInodes);
}).catch((err: BusinessError): void => {
  console.error(`getTotalInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

