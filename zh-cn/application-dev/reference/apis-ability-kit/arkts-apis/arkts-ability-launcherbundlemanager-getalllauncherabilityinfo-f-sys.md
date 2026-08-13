# getAllLauncherAbilityInfo（系统接口）

## getAllLauncherAbilityInfo

```TypeScript
function getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>) : void
```

查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-launcherBundleManager-function getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>) : void--><!--Device-launcherBundleManager-function getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>) : void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 被查询的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)。当函数调用成功，err为 undefined，data为指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)信息 。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  launcherBundleManager.getAllLauncherAbilityInfo(100,
    (errData: BusinessError, data: launcherBundleManager.LauncherAbilityInfo[]) => {
      if (errData !== null) {
        console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
      } else {
        console.info('data is ' + JSON.stringify(data));
      }
    });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 代码中使用的useId需为应用实际的用户ID。
try {
  launcherBundleManager.getAllLauncherAbilityInfo(100, (errData, data) => {
    if (errData !== null) {
      console.error(`getAllLauncherAbilityInfo errData is errCode:${errData.code}  message:${errData.message}`);
    } else {
      console.info('getAllLauncherAbilityInfo data is ' + JSON.stringify(data));
    }
  });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`getAllLauncherAbilityInfo errData is errCode:${code}  message:${message}`);
}
```


## getAllLauncherAbilityInfo

```TypeScript
function getAllLauncherAbilityInfo(userId: int) : Promise<Array<LauncherAbilityInfo>>
```

查询指定用户下所有应用的[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-launcherBundleManager-function getAllLauncherAbilityInfo(userId: int) : Promise<Array<LauncherAbilityInfo>>--><!--Device-launcherBundleManager-function getAllLauncherAbilityInfo(userId: int) : Promise<Array<LauncherAbilityInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 被查询的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;LauncherAbilityInfo&gt;&gt; | Promise对象。返回指定用户下所有应用的 [LauncherAbilityInfo]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not support. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  launcherBundleManager.getAllLauncherAbilityInfo(100)
    .then((data: launcherBundleManager.LauncherAbilityInfo[]) => {
      console.info('data is ' + JSON.stringify(data));
    }).catch((errData: BusinessError) => {
      console.error(`errData is errCode:${errData.code}  message:${errData.message}`);
    });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 代码中使用的useId需为应用实际的用户ID。
try {
  launcherBundleManager.getAllLauncherAbilityInfo(100)
    .then((data: launcherBundleManager.LauncherAbilityInfo[]) => {
      console.info('getAllLauncherAbilityInfo data is ' + JSON.stringify(data));
    }).catch ((errData: Error) => {
      console.error(`getAllLauncherAbilityInfo errData is errCode:${(errData as BusinessError).code}  message:${(errData as BusinessError).message}`);
    });
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`getAllLauncherAbilityInfo errData is errCode:${code}  message:${message}`);
}
```

