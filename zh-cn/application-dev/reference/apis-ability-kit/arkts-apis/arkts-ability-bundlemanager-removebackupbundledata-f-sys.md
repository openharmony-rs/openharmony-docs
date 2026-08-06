# removeBackupBundleData（系统接口）

## removeBackupBundleData

```TypeScript
function removeBackupBundleData(bundleName: string, userId: int, appIndex: int): Promise<void>
```

删除指定用户下指定应用或分身应用的备份数据。使用Promise异步回调。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CLEAN_APPLICATION_DATA

<!--Device-bundleManager-function removeBackupBundleData(bundleName: string, userId: int, appIndex: int): Promise<void>--><!--Device-bundleManager-function removeBackupBundleData(bundleName: string, userId: int, appIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要删除备份的应用包名。 |
| userId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示用户ID，可以通过[getOsAccountLocalId]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取，取值范围：大于等于0。 |
| appIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示应用索引。取值范围0~5，取值为0表示主应用，取值1~5表示分身应用的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际的包名、用户ID和应用索引
let bundleName: string = 'com.ohos.demo';
let userId: number = 100;
let appIndex: number = 0;

try {
  bundleManager.removeBackupBundleData(bundleName, userId, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'removeBackupBundleData successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'removeBackupBundleData failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'removeBackupBundleData failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际的包名、用户ID和应用索引
let bundleName: string = 'com.ohos.demo';
let userId: int = 100;
let appIndex: int = 0;

try {
  bundleManager.removeBackupBundleData(bundleName, userId, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'removeBackupBundleData successfully');
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'removeBackupBundleData failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'removeBackupBundleData failed. Cause: %{public}s', message);
}
```

