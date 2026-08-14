# getApplicationInfoSync（系统接口）

## getApplicationInfoSync

```TypeScript
function getApplicationInfoSync(bundleName: string, applicationFlags: int, userId: int) : ApplicationInfo
```

以同步方法根据给定的bundleName、applicationFlags和userId获取ApplicationInfo。 获取调用方自身的信息时不需要权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getApplicationInfoSync(bundleName: string, applicationFlags: int, userId: int) : ApplicationInfo--><!--Device-bundleManager-function getApplicationInfoSync(bundleName: string, applicationFlags: int, userId: int) : ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用程序的bundleName。 |
| applicationFlags | int | 是 | 表示用于指定将返回的ApplicationInfo对象中包含的信息，具体取值及不同含义参考 [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag（系统接口）)。 |
| userId | int | 是 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ApplicationInfo | 返回ApplicationInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let applicationFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;
let userId = 100;

try {
  let data = bundleManager.getApplicationInfoSync(bundleName, applicationFlags, userId);
  hilog.info(0x0000, 'testTag', 'getApplicationInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfoSync failed: %{public}s', message);
}
```


## getApplicationInfoSync

```TypeScript
function getApplicationInfoSync(bundleName: string, applicationFlags: int) : ApplicationInfo
```

以同步方法根据给定的bundleName、applicationFlags获取ApplicationInfo。 获取调用方自身的信息时不需要权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getApplicationInfoSync(bundleName: string, applicationFlags: int) : ApplicationInfo--><!--Device-bundleManager-function getApplicationInfoSync(bundleName: string, applicationFlags: int) : ApplicationInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示应用程序的bundleName。 |
| applicationFlags | int | 是 | 表示用于指定将返回的ApplicationInfo对象中包含的信息，具体取值及不同含义参考 [ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md#ApplicationFlag（系统接口）)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ApplicationInfo | 返回ApplicationInfo对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let applicationFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  let data = bundleManager.getApplicationInfoSync(bundleName, applicationFlags);
  hilog.info(0x0000, 'testTag', 'getApplicationInfoSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfoSync failed: %{public}s', message);
}
```

