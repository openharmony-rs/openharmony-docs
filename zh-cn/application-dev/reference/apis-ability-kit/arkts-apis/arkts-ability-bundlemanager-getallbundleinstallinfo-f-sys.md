# getAllBundleInstallInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleInstallInfo

```TypeScript
function getAllBundleInstallInfo(): Promise<Array<Record<string, Object>>>
```

获取系统内所有应用的扩展安装信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAllBundleInstallInfo(): Promise<Array<Record<string, Object>>>--><!--Device-bundleManager-function getAllBundleInstallInfo(): Promise<Array<Record<string, Object>>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Record&lt;string, Object&gt;&gt;&gt; | The install information. |

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
  bundleManager.getAllBundleInstallInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllBundleInstallInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleInstallInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInstallInfo failed. Cause: %{public}s', message);
}

```

