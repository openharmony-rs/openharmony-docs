# getAllSharedBundleInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllSharedBundleInfo

```TypeScript
function getAllSharedBundleInfo(callback: AsyncCallback<Array<SharedBundleInfo>>): void
```

获取所有的共享包信息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllSharedBundleInfo(callback: AsyncCallback<Array<SharedBundleInfo>>): void--><!--Device-bundleManager-function getAllSharedBundleInfo(callback: AsyncCallback<Array<SharedBundleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;SharedBundleInfo&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)，当获取成功时 ，err为undefined，data为获所有的共享包信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllSharedBundleInfo((err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllSharedBundleInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed: %{public}s', message);
}
```


## getAllSharedBundleInfo

```TypeScript
function getAllSharedBundleInfo(): Promise<Array<SharedBundleInfo>>
```

获取所有的共享包信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllSharedBundleInfo(): Promise<Array<SharedBundleInfo>>--><!--Device-bundleManager-function getAllSharedBundleInfo(): Promise<Array<SharedBundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;SharedBundleInfo&gt;&gt; | Promise对象，返回所有的共享包信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllSharedBundleInfo().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllSharedBundleInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed. Cause: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAllSharedBundleInfo().then((data: Array<bundleManager.SharedBundleInfo>) => {
    hilog.info(0x0000, 'testTag', 'getAllSharedBundleInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllSharedBundleInfo failed. Cause: %{public}s', message);
}
```

