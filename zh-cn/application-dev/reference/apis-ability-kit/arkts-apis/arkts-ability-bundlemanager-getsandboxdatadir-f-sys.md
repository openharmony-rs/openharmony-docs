# getSandboxDataDir（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getSandboxDataDir

```TypeScript
function getSandboxDataDir(bundleName: string, appIndex: number): string
```

根据应用包名和分身索引获取对应的沙箱目录。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getSandboxDataDir(bundleName: string, appIndex: int): string--><!--Device-bundleManager-function getSandboxDataDir(bundleName: string, appIndex: int): string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的应用包名。当前用户下有此应用或者分身才可查询，否则返回错误码17700001。 |
| appIndex | number | 是 | 应用索引，用于标识不同的应用实例。取值为整数。<br>取值范围：<br>- 0：主应用<br> - [1, 5]：分身应用<br>- [2000, 3000]：沙箱应用（API版本26.0.0支持） |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回应用的沙箱目录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appIndex = 1;

try {
  let dataDir = bundleManager.getSandboxDataDir(bundleName, appIndex);
  hilog.info(0x0000, 'testTag', 'getSandboxDataDir successfully. dataDir:%{public}s', dataDir);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSandboxDataDir failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
