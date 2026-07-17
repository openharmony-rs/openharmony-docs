# getBundleInfoSync

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getBundleInfoSync

```TypeScript
function getBundleInfoSync(bundleName: string, bundleFlags: number, userId: number): BundleInfo
```

以同步方法根据给定的bundleName、bundleFlags和userId获取BundleInfo。

获取调用方自身的信息时不需要权限。

**起始版本：** 14

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getBundleInfoSync(bundleName: string, bundleFlags: int, userId: int): BundleInfo--><!--Device-bundleManager-function getBundleInfoSync(bundleName: string, bundleFlags: int, userId: int): BundleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的应用Bundle名称。 |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息。 |
| userId | number | 是 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleInfo](arkts-ability-bundleinfo-i.md) | 返回BundleInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION;
let userId = 100;

try {
  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  hilog.info(0x0000, 'testTag', 'getBundleInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoSync failed: %{public}s', message);
}

```


## getBundleInfoSync

```TypeScript
function getBundleInfoSync(bundleName: string, bundleFlags: number): BundleInfo
```

以同步方法根据给定的bundleName、bundleFlags获取调用方所在用户下的BundleInfo。

获取调用方自身的信息时不需要权限。

**起始版本：** 14

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getBundleInfoSync(bundleName: string, bundleFlags: int): BundleInfo--><!--Device-bundleManager-function getBundleInfoSync(bundleName: string, bundleFlags: int): BundleInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的应用Bundle名称。 |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BundleInfo](arkts-ability-bundleinfo-i.md) | 返回BundleInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION;
try {
  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags);
  hilog.info(0x0000, 'testTag', 'getBundleInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoSync failed: %{public}s', message);
}

```

