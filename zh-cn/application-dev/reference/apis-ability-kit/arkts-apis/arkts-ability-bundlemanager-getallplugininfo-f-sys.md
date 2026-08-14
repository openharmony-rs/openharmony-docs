# getAllPluginInfo（系统接口）

## getAllPluginInfo

```TypeScript
function getAllPluginInfo(hostBundleName: string, userId?: int): Promise<Array<PluginBundleInfo>>
```

根据给定的hostBundleName和userId获取所有的PluginBundleInfo。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllPluginInfo(hostBundleName: string, userId?: int): Promise<Array<PluginBundleInfo>>--><!--Device-bundleManager-function getAllPluginInfo(hostBundleName: string, userId?: int): Promise<Array<PluginBundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostBundleName | string | 是 | 表示安装插件的应用包名。 |
| userId | int | 否 | 表示用户ID，可以通过 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取，默认值：调用方所在用户ID。取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PluginBundleInfo&gt;&gt; | Promise对象，返回Array&lt;PluginBundleInfo&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

let hostBundleName = 'com.ohos.demo';
let userId = 100;

try {
  bundleManager.getAllPluginInfo(hostBundleName, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}
```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let hostBundleName = 'com.ohos.demo';

try {
  bundleManager.getAllPluginInfo(hostBundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 代码中使用的hostBundleName、useId需为应用实际的包名、用户ID。
let hostBundleName = 'com.ohos.demo';
let userId = 100;

try {
  bundleManager.getAllPluginInfo(hostBundleName, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}
```

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 代码中使用的hostBundleName需为应用实际的包名。
let hostBundleName = 'com.ohos.demo';

try {
  bundleManager.getAllPluginInfo(hostBundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllPluginInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllPluginInfo failed. Cause: %{public}s', message);
}
```

