# getAllNewPreinstalledApplicationInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllNewPreinstalledApplicationInfo

```TypeScript
function getAllNewPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>
```

获取设备OTA升级期间当前用户下新增的所有预置应用信息。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAllNewPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>--><!--Device-bundleManager-function getAllNewPreinstalledApplicationInfo(): Promise<Array<PreinstalledApplicationInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PreinstalledApplicationInfo&gt;&gt; | Promise对象，设备OTA升级期间当前用户下新增的所有预置应用信息。 |

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
  bundleManager.getAllNewPreinstalledApplicationInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo success, Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllNewPreinstalledApplicationInfo failed: %{public}s', message);
}

```

