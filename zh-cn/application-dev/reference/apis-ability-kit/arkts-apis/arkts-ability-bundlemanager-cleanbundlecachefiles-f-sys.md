# cleanBundleCacheFiles（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void
```

根据给定的bundleName清理BundleCache。使用callback异步回调。

调用方清理自身缓存数据时不需要权限。

**起始版本：** 9

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要清理其缓存数据的应用程序的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当清理应用缓存目录数据成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-指定的应用不支持清除缓存文件) | The specified bundle does not support clearing of cache files. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName, err => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```


## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string): Promise<void>
```

根据给定的bundleName清理BundleCache。使用Promise异步回调。

调用方清理自身缓存数据时不需要权限。

**起始版本：** 9

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string): Promise<void>--><!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要清理其缓存数据的应用程序的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-指定的应用不支持清除缓存文件) | The specified bundle does not support clearing of cache files. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```


## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, appIndex: number): Promise<void>
```

根据给定的bundleName和appIndex清理BundleCache。使用Promise异步回调。

调用方清理自身缓存数据时不需要权限。

**起始版本：** 15

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

<!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string, appIndex: int): Promise<void>--><!--Device-bundleManager-function cleanBundleCacheFiles(bundleName: string, appIndex: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要清理其缓存数据的应用程序的bundleName。 |
| appIndex | number | 是 | 表示要清理其缓存数据的应用程序的分身应用索引。<br>appIndex为0时，表示清理主应用缓存数据。appIndex大于0时，表示清理指定分身应用缓存数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700030](../errorcode-bundle.md#17700030-指定的应用不支持清除缓存文件) | The specified bundle does not support clearing of cache files. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";
let appIndex = 1;

try {
  bundleManager.cleanBundleCacheFiles(bundleName, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```

