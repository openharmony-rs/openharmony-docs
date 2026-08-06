# getAllExtBundleStats（系统接口）

## getAllExtBundleStats

```TypeScript
function getAllExtBundleStats(userId: int): Promise<Array<ExtBundleStats>>
```

获取指定用户下所有系统应用或系统服务的空间占用详情。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.STORAGE_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getAllExtBundleStats(userId: int): Promise<Array<ExtBundleStats>>--><!--Device-storageStatistics-function getAllExtBundleStats(userId: int): Promise<Array<ExtBundleStats>>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 用户id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ExtBundleStats&gt;&gt; | Promise对象，返回指定用户下所有系统应用或系统服务的空间占用详情。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600010 | The input parameter is invalid. |
| 13600013 | Failed to query all business space usage. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
storageStatistics.getAllExtBundleStats(userId).then((bundleStatsList: storageStatistics.ExtBundleStats[]) => {
  console.info("getAllExtBundleStats successfully");
}).catch((err: BusinessError) => {
  console.error(`getAllExtBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userId: int = 100;
storageStatistics.getAllExtBundleStats(userId).then((bundleStatsList: storageStatistics.ExtBundleStats[]) => {
  console.info("getAllExtBundleStats successfully");
}).catch((err: BusinessError): void => {
  console.error(`getAllExtBundleStats failed with err, code is: ${err.code}, message is: ${err.message}`);
});
```

