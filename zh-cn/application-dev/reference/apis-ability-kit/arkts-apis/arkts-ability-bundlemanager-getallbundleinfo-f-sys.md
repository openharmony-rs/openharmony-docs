# getAllBundleInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlags: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

根据给定的bundleFlags获取系统中所有的BundleInfo。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, callback: AsyncCallback<Array<BundleInfo>>): void--><!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, callback: AsyncCallback<Array<BundleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<BundleInfo>> | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为undefined，data为获取到的Array&lt;BundleInfo&gt;；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  bundleManager.getAllBundleInfo(bundleFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllBundleInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed: %{public}s', message);
}

```


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlags: number, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

根据给定的bundleFlags和userId获取系统中所有的BundleInfo。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, userId: int, callback: AsyncCallback<Array<BundleInfo>>): void--><!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, userId: int, callback: AsyncCallback<Array<BundleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息。 |
| userId | number | 是 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<BundleInfo>> | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为undefined，data为获取到的Array&lt;BundleInfo&gt;；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION;
let userId = 100;

try {
  bundleManager.getAllBundleInfo(bundleFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllBundleInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed: %{public}s', message);
}

```


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlags: number, userId?: number): Promise<Array<BundleInfo>>
```

根据给定的bundleFlags和userId获取系统中所有的BundleInfo。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, userId?: int): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getAllBundleInfo(bundleFlags: int, userId?: int): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息。 |
| userId | number | 否 | 表示用户ID，可以通过[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)获取，默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<BundleInfo>> | Promise对象。返回Array&lt;BundleInfo&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  bundleManager.getAllBundleInfo(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllBundleInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfo failed. Cause: %{public}s', message);
}

```

