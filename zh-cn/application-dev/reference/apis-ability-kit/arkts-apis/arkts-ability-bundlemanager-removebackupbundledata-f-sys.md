# removeBackupBundleData（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="removebackupbundledata"></a>
## removeBackupBundleData

```TypeScript
function removeBackupBundleData(bundleName: string, userId: number, appIndex: number): Promise<void>
```

删除指定用户下指定应用或分身应用的备份数据。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.CLEAN_APPLICATION_DATA

<!--Device-bundleManager-function removeBackupBundleData(bundleName: string, userId: int, appIndex: int): Promise<void>--><!--Device-bundleManager-function removeBackupBundleData(bundleName: string, userId: int, appIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要删除备份的应用包名。 |
| userId | number | 是 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取，取值范围：大于等于0。 |
| appIndex | number | 是 | 表示应用索引。取值范围0~5，取值为0表示主应用，取值1~5表示分身应用的索引。 |

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

