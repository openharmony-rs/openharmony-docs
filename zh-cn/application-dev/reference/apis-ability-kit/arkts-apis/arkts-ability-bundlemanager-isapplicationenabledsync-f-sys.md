# isApplicationEnabledSync（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## isApplicationEnabledSync

```TypeScript
function isApplicationEnabledSync(bundleName: string): boolean
```

以同步方法获取指定应用的禁用或使能状态。

**起始版本：** 10

<!--Device-bundleManager-function isApplicationEnabledSync(bundleName: string): boolean--><!--Device-bundleManager-function isApplicationEnabledSync(bundleName: string): boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用程序的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前应用为使能状态，返回false表示当前应用为禁用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  let data = bundleManager.isApplicationEnabledSync(bundleName);
  hilog.info(0x0000, 'testTag', 'isApplicationEnabledSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationEnabledSync failed: %{public}s', message);
}

```

