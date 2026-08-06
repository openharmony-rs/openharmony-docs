# getCurrentBundleInodes

## getCurrentBundleInodes

```TypeScript
function getCurrentBundleInodes(): Promise<long>
```

获取当前应用的inode占用量，使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-storageStatistics-function getCurrentBundleInodes(): Promise<long>--><!--Device-storageStatistics-function getCurrentBundleInodes(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.SpatialStatistics

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象，返回当前应用的inode占用量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. |
| 13600002 | File system not supported. |
| 13600017 | Failed to query the inode information of the application. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleInodes().then((curInodes: number) => {
  console.info('getCurrentBundleInodes successfully:' + curInodes);
}).catch((err: BusinessError) => {
  console.error(`getCurrentBundleInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

storageStatistics.getCurrentBundleInodes().then((curInodes: long) => {
  console.info('getCurrentBundleInodes successfully:' + curInodes);
}).catch((err: BusinessError): void => {
  console.error(`getCurrentBundleInodes failed. Code: ${err.code}, message: ${err.message}`);
});
```

