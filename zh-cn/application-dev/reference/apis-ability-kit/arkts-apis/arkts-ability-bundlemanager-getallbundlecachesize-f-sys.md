# getAllBundleCacheSize（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleCacheSize

```TypeScript
function getAllBundleCacheSize(): Promise<number>
```

获取全局缓存大小，单位：字节。使用Promise异步回调。

有程序运行时的应用的缓存、或者在[应用配置指南](../../../../../device-dev/subsystems/subsys-app-privilege-config-guide.md)中已配置“AllowAppDataNotCleared”特权的应用的缓存，无法被获取。

**起始版本：** 15

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllBundleCacheSize(): Promise<long>--><!--Device-bundleManager-function getAllBundleCacheSize(): Promise<long>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回全局缓存大小，以字节为单位。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

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

