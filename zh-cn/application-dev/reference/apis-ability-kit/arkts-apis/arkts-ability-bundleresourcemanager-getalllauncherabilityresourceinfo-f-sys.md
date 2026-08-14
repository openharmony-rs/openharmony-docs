# getAllLauncherAbilityResourceInfo（系统接口）

## getAllLauncherAbilityResourceInfo

```TypeScript
function getAllLauncherAbilityResourceInfo(resourceFlags: int, callback: AsyncCallback<Array<LauncherAbilityResourceInfo>>): void
```

根据给定的resourceFlags获取当前所有应用的LauncherAbilityResourceInfo。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getAllLauncherAbilityResourceInfo(resourceFlags: int, callback: AsyncCallback<Array<LauncherAbilityResourceInfo>>): void--><!--Device-bundleResourceManager-function getAllLauncherAbilityResourceInfo(resourceFlags: int, callback: AsyncCallback<Array<LauncherAbilityResourceInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | int | 是 | 指定返回的LauncherAbilityResourceInfo所包含的信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;LauncherAbilityResourceInfo&gt;&gt; | 是 | [回调函数](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当获取成 功时，err为undefined，data为获取到的LauncherAbilityResourceInfo数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s', JSON.stringify(data?.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```


## getAllLauncherAbilityResourceInfo

```TypeScript
function getAllLauncherAbilityResourceInfo(resourceFlags: int): Promise<Array<LauncherAbilityResourceInfo>>
```

根据给定的resourceFlags获取当前所有应用的LauncherAbilityResourceInfo。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getAllLauncherAbilityResourceInfo(resourceFlags: int): Promise<Array<LauncherAbilityResourceInfo>>--><!--Device-bundleResourceManager-function getAllLauncherAbilityResourceInfo(resourceFlags: int): Promise<Array<LauncherAbilityResourceInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | int | 是 | 指定返回的LauncherAbilityResourceInfo所包含的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;LauncherAbilityResourceInfo&gt;&gt; | Promise对象，返回LauncherAbilityResourceInfo数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag).then((data: Array<bundleResourceManager.LauncherAbilityResourceInfo>) => {
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s', JSON.stringify(data.length));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', (err as BusinessError).message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

