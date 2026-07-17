# cleanAllBundleCache（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## cleanAllBundleCache

```TypeScript
function cleanAllBundleCache(): Promise<void>
```

清理全局缓存。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundleManager-function cleanAllBundleCache(): Promise<void>--><!--Device-bundleManager-function cleanAllBundleCache(): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

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
  bundleManager.cleanAllBundleCache().then((data) => {
    hilog.info(0x0000, 'testTag', 'cleanAllBundleCache successful.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanAllBundleCache failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanAllBundleCache failed: %{public}s', message);
}

```

