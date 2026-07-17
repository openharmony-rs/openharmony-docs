# getBundleInstallStatus（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleInstallStatus

```TypeScript
function getBundleInstallStatus(bundleName: string): BundleInstallStatus
```

查询当前用户下指定应用的安装状态。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getBundleInstallStatus(bundleName: string): BundleInstallStatus--><!--Device-bundleManager-function getBundleInstallStatus(bundleName: string): BundleInstallStatus-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定应用的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleInstallStatus](arkts-ability-bundlemanager-bundleinstallstatus-e-sys.md) | 应用的安装状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际的包名
let bundleName: string = 'com.ohos.demo';

try {
  let bundleInstallStatus = bundleManager.getBundleInstallStatus(bundleName);
  hilog.info(0x0000, 'testTag', 'bundle install status:' + bundleInstallStatus);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInstallStatus failed. Cause: %{public}s', message);
}

```

