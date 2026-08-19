# getAppCloneIdentity

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAppCloneIdentity

```TypeScript
function getAppCloneIdentity(uid: int): Promise<AppCloneIdentity>
```

根据uid查询分身应用的包名和分身索引。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getAppCloneIdentity(uid: int): Promise<AppCloneIdentity>--><!--Device-bundleManager-function getAppCloneIdentity(uid: int): Promise<AppCloneIdentity>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | 表示应用程序的UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AppCloneIdentity&gt; | Promise对象，返回&lt;AppCloneIdentity&gt;。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700021](../errorcode-bundle.md#17700021-指定的uid无效) | The uid is not found. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005;

try {
  bundleManager.getAppCloneIdentity(uid).then((res) => {
    hilog.info(0x0000, 'testTag', 'getAppCloneIdentity res = %{public}s', JSON.stringify(res));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 代码中使用的uid需为应用实际的uid。
let uid = 20010005;

try {
  bundleManager.getAppCloneIdentity(uid).then((res: bundleManager.AppCloneIdentity) => {
    hilog.info(0x0000, 'testTag', 'getAppCloneIdentity res = %{public}s', JSON.stringify(res));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAppCloneIdentity failed. Cause: %{public}s', message);
}
```

