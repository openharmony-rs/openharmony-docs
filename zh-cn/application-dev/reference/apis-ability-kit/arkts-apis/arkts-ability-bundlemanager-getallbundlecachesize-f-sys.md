# getAllBundleCacheSize（系统接口）

## getAllBundleCacheSize

```TypeScript
function getAllBundleCacheSize(): Promise<long>
```

获取全局缓存大小，单位：字节。使用Promise异步回调。 有程序运行时的应用的缓存、或者在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中已配置“ AllowAppDataNotCleared”特权的应用的缓存，无法被获取。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllBundleCacheSize(): Promise<long>--><!--Device-bundleManager-function getAllBundleCacheSize(): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;long&gt; | Promise对象。返回全局缓存大小，以字节为单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllBundleCacheSize().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllBundleCacheSize successful. Data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllBundleCacheSize().then((data: long) => {
    hilog.info(0x0000, 'testTag','getAllBundleCacheSize successful. Data: ' + JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleCacheSize failed: %{public}s', message);
}
```

