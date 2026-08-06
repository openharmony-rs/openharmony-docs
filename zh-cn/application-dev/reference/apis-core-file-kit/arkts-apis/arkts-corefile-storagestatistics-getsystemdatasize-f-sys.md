# getSystemDataSize（系统接口）

## getSystemDataSize

```TypeScript
function getSystemDataSize(): Promise<long>
```

获取系统数据的总空间大小，使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**需要权限：** ohos.permission.STORAGE_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getSystemDataSize(): Promise<long>--><!--Device-storageStatistics-function getSystemDataSize(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回系统数据的总空间大小，单位：Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600018 | Failed to query the system data size. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemDataSize().then((systemDataSize: number) => {
  console.info("getSystemDataSize successfully: " + systemDataSize);
}).catch((err: BusinessError) => {
  console.error(`getSystemDataSize failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getSystemDataSize().then((systemDataSize: long) => {
  console.info("getSystemDataSize successfully: " + systemDataSize);
}).catch((err: BusinessError): void => {
  console.error(`getSystemDataSize failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

