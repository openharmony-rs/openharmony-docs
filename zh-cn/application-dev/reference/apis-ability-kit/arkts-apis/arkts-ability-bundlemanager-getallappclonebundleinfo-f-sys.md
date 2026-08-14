# getAllAppCloneBundleInfo（系统接口）

## getAllAppCloneBundleInfo

```TypeScript
function getAllAppCloneBundleInfo(bundleName: string, bundleFlags: int, userId?: int): Promise<Array<BundleInfo>>
```

根据bundleName、[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)以及用户ID查询主应用和分身应用的BundleInfo列表。 使用Promise异步回调。 获取调用方自身的信息时不需要权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllAppCloneBundleInfo(bundleName: string, bundleFlags: int, userId?: int): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getAllAppCloneBundleInfo(bundleName: string, bundleFlags: int, userId?: int): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的应用Bundle名称。 |
| bundleFlags | int | 是 | 表示用于指定要返回的BundleInfo对象中包含的信息的标志。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取，默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise对象。返回应用包信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle and clone apps are all disabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_HAP_MODULE |
bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY;

try {
  bundleManager.getAllAppCloneBundleInfo(bundleName, bundleFlags).then((res: Array<bundleManager.BundleInfo>) => {
    let index = 0;
    for (let item of res) {
      hilog.info(0x0000, 'testTag', 'getAllAppCloneBundleInfo res: BundleInfo[%{public}d] = %{public}s', index++,
        JSON.stringify(item));
    }
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllAppCloneBundleInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllAppCloneBundleInfo failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
// 代码中使用的bundleName需为应用实际的包名。
let bundleName = 'com.example.myapplication';
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_HAP_MODULE |
bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY;

try {
  bundleManager.getAllAppCloneBundleInfo(bundleName, bundleFlags).then((res: Array<bundleManager.BundleInfo>) => {
    let index = 0;
    for (let item of res) {
      hilog.info(0x0000, 'testTag', 'getAllAppCloneBundleInfo res: BundleInfo[%{public}d] = %{public}s', index++, JSON.stringify(item));
    }
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllAppCloneBundleInfo failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllAppCloneBundleInfo failed. Cause: %{public}s', message);
}
```

