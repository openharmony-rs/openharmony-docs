# isApplicationDisableForbidden（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## isApplicationDisableForbidden

```TypeScript
function isApplicationDisableForbidden(bundleName: string, userId: number, appIndex: number): boolean
```

以同步方法查询指定用户下指定应用或分身应用是否被设置禁止停用。

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or (ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function isApplicationDisableForbidden(bundleName: string, userId: int, appIndex: int): boolean--><!--Device-bundleManager-function isApplicationDisableForbidden(bundleName: string, userId: int, appIndex: int): boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用的包名。 |
| userId | number | 是 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取，取值范围：大于等于0。 |
| appIndex | number | 是 | 表示应用索引。取值范围0~5，取值为0表示主应用，取值1~5表示分身应用的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 指定应用是否被设置禁止停用。<br/>返回true表示指定应用已被设置禁止停用，返回false表示指定应用没有被设置禁止停用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Non-system APP calling system API. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.example.myapplication';
let userId: number = 100;
let appIndex: number = 0;

try {
  let data = bundleManager.isApplicationDisableForbidden(bundleName, userId, appIndex);
  hilog.info(0x0000, 'testTag', 'isApplicationDisableForbidden successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationDisableForbidden failed: %{public}s', message);
}


```

