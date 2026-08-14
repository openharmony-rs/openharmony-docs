# getAllApplicationInfo（系统接口）

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: int, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

根据给定的appFlags获取系统中所有的ApplicationInfo。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllApplicationInfo(appFlags: int, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundleManager-function getAllApplicationInfo(appFlags: int, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appFlags | int | 是 | 指定返回的ApplicationInfo所包含的信息，具体取值及不同含义参考 [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag（系统接口）)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当获取成功时， err为undefined，data为获取到的Array&lt;ApplicationInfo&gt;；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  bundleManager.getAllApplicationInfo(appFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', message);
}
```


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: int,
    userId: int, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

根据给定的appFlags和userId获取系统中所有的ApplicationInfo。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllApplicationInfo(appFlags: int,    userId: int, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundleManager-function getAllApplicationInfo(appFlags: int,    userId: int, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appFlags | int | 是 | 指定返回的ApplicationInfo所包含的信息，具体取值及不同含义参考 [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag（系统接口）)。 |
| userId | int | 是 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当获取成功时， err为undefined，data为获取到的Array&lt;ApplicationInfo&gt;；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;
let userId = 100;

try {
  bundleManager.getAllApplicationInfo(appFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', message);
}
```


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: int, userId?: int): Promise<Array<ApplicationInfo>>
```

根据给定的appFlags和userId获取系统中所有的ApplicationInfo。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST

<!--Device-bundleManager-function getAllApplicationInfo(appFlags: int, userId?: int): Promise<Array<ApplicationInfo>>--><!--Device-bundleManager-function getAllApplicationInfo(appFlags: int, userId?: int): Promise<Array<ApplicationInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appFlags | int | 是 | 指定返回的ApplicationInfo所包含的信息，具体取值及不同含义参考 [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag（系统接口）)。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取，默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ApplicationInfo&gt;&gt; | Promise对象，返回Array&lt;ApplicationInfo&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  bundleManager.getAllApplicationInfo(appFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  bundleManager.getAllApplicationInfo(appFlags).then((data: Array<bundleManager.ApplicationInfo>) => {
    hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', message);
}
```

