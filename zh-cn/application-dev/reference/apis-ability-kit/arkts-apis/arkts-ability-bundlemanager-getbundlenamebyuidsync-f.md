# getBundleNameByUidSync

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleNameByUidSync

```TypeScript
function getBundleNameByUidSync(uid: int): string
```

以同步方法根据给定的uid获取对应应用的bundleName。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getBundleNameByUidSync(uid: int): string--><!--Device-bundleManager-function getBundleNameByUidSync(uid: int): string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | 表示应用程序的UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回获取到的bundleName。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700021](../errorcode-bundle.md#17700021-指定的uid无效) | The uid is not found. |

**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005;
try {
  let data = bundleManager.getBundleNameByUidSync(uid);
  hilog.info(0x0000, 'testTag', 'getBundleNameByUidSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleNameByUidSync failed. Cause: %{public}s', message);
}
```

