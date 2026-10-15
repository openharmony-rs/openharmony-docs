# setAdditionalInfoByIndex（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAdditionalInfoByIndex

```TypeScript
function setAdditionalInfoByIndex(bundleName: string, additionalInfo: string, appIndex: number): void
```

设置指定应用实例的附加信息。该接口仅支持应用市场调用。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function setAdditionalInfoByIndex(bundleName: string, additionalInfo: string, appIndex: int): void--><!--Device-bundleManager-function setAdditionalInfoByIndex(bundleName: string, additionalInfo: string, appIndex: int): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 包名。 |
| additionalInfo | string | 是 | 要设置的其他信息。 |
| appIndex | number | 是 | Index of the application mode.The value must be equal to 0 or 10000.<br>取值限定为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700053](../errorcode-bundle.md#17700053-非应用市场调用) | The caller is not AppGallery. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let additionalInfo = "xxxxxxxxx,formUpdateLevel:4";
let appIndex = 0;

try {
  bundleManager.setAdditionalInfoByIndex(bundleName, additionalInfo, appIndex);
  hilog.info(0x0000, 'testTag', 'setAdditionalInfoByIndex successfully.');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAdditionalInfoByIndex failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
