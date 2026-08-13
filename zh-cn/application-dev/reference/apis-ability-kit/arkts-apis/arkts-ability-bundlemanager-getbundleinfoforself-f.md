# getBundleInfoForSelf

## getBundleInfoForSelf

```TypeScript
function getBundleInfoForSelf(bundleFlags: int): Promise<BundleInfo>
```

根据给定的bundleFlags获取当前应用的BundleInfo。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function getBundleInfoForSelf(bundleFlags: int): Promise<BundleInfo>--><!--Device-bundleManager-function getBundleInfoForSelf(bundleFlags: int): Promise<BundleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | int | 是 | 指定返回的BundleInfo所包含的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | Promise对象，返回当前应用的BundleInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

ArkTS-Dyn示例:

```TypeScript
// 获取bundleInfo，包含带有metadataArray信息的appInfo信息
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags =
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION | bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA;

try {
  bundleManager.getBundleInfoForSelf(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', message);
}
```

ArkTS-Sta示例:

```TypeScript
'use static'

// 获取bundleInfo，包含带有metadataArray信息的appInfo信息
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags =
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION | bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA;

try {
  bundleManager.getBundleInfoForSelf(bundleFlags).then((data: bundleManager.BundleInfo) => {
    hilog.info(0x0000, 'testTag', 'getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: Error) => {
    hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed. Cause: %{public}s', (err as BusinessError).message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', message);
}
```


## getBundleInfoForSelf

```TypeScript
function getBundleInfoForSelf(bundleFlags: int, callback: AsyncCallback<BundleInfo>): void
```

根据给定的bundleFlags获取当前应用的BundleInfo。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function getBundleInfoForSelf(bundleFlags: int, callback: AsyncCallback<BundleInfo>): void--><!--Device-bundleManager-function getBundleInfoForSelf(bundleFlags: int, callback: AsyncCallback<BundleInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | int | 是 | 指定返回的BundleInfo所包含的信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;BundleInfo&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md#AsyncCallback)，当获取成功时，err为 undefined，data为获取到的当前应用的BundleInfo；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

## 示例

```TypeScript
// 获取bundleInfo，包含permissions信息的abilitiesInfo信息
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags =
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_HAP_MODULE | bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_ABILITY |
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION;

try {
  bundleManager.getBundleInfoForSelf(bundleFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleInfoForSelf successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', message);
}
```

