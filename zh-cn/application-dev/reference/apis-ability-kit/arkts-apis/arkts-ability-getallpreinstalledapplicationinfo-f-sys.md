# getAllPreinstalledApplicationInfo（系统接口）

## getAllPreinstalledApplicationInfo

```TypeScript
function getAllPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>
```

获取所有预置应用信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PreinstalledApplicationInfo&gt;&gt; | Promise对象，返回Array&lt;PreinstalledApplicationInfo&gt;。 |

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
  bundleManager.getAllPreinstalledApplicationInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo success, Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPreinstalledApplicationInfo failed: %{public}s', message);
}

```

