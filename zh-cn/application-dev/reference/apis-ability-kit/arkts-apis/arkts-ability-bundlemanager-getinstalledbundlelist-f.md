# getInstalledBundleList

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="getinstalledbundlelist"></a>
## getInstalledBundleList

```TypeScript
function getInstalledBundleList(bundleFlags: number): Promise<Array<BundleInfo>>
```

根据给定的bundleFlags获取系统中所有的BundleInfo。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_GET_INSTALLED_BUNDLE_LIST

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getInstalledBundleList(bundleFlags: int): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getInstalledBundleList(bundleFlags: int): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 指定返回的BundleInfo所包含的信息，详情请参考[BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise对象，返回当前已安装应用的信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  bundleManager.getInstalledBundleList(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getInstalledBundleList successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getInstalledBundleList failed. Cause: %{public}s', message);
}

```

