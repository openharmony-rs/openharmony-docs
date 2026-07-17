# getCurrentBundleInodes

## 导入模块

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## getCurrentBundleInodes

```TypeScript
function getCurrentBundleInodes(): Promise<number>
```

获取当前应用的inode占用量，使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getCurrentBundleInodes(): Promise<long>--><!--Device-storageStatistics-function getCurrentBundleInodes(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回当前应用的inode占用量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13600002 | File system not supported. |
| 13600017 | Failed to query the inode information of the application. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleInodes().then((bundleInodes: number) => {
  console.info('getCurrentBundleInodes successfully:' + bundleInodes);
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleInodes failed. Code: ${err.code}, message: ${err.message}`);
});

```

