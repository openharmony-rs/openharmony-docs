# switchUninstallState（系统接口）

## switchUninstallState

```TypeScript
function switchUninstallState(bundleName: string, state: boolean): void
```

切换指定应用的可卸载状态，此接口与EDM应用拦截管控机制不互相影响。

**起始版本：** 12

**需要权限：** ohos.permission.CHANGE_BUNDLE_UNINSTALL_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示指定应用的bundleName。 |
| state | boolean | 是 | 表示应用的可卸载状态，值为true表示应用可以被卸载，值为false表示应用不可以被卸载。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700060](../errorcode-bundle.md#17700060-指定的应用不允许被卸载) | The specified application cannot be uninstalled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  bundleManager.switchUninstallState('com.example.myapplication', false);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'switchUninstallState failed: %{public}s', message);
}

```

