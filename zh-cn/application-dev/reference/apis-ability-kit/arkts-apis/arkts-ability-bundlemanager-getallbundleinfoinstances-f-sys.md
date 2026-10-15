# getAllBundleInfoInstances（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllBundleInfoInstances

```TypeScript
function getAllBundleInfoInstances(bundleName: string, bundleFlags: number): Promise<Array<BundleInfo>>
```

根据给定的套餐名称和套餐标志，获取系统中所有的套餐信息。该接口使用了一个类型的promise来返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAllBundleInfoInstances(bundleName: string, bundleFlags: int): Promise<Array<BundleInfo>>--><!--Device-bundleManager-function getAllBundleInfoInstances(bundleName: string, bundleFlags: int): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 包名。 |
| bundleFlags | number | 是 | Type of the bundle information to obtain.<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md)&gt;&gt; | Promise 用于返回bundle信息的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

<!--Del-->
**示例**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT |
  bundleManager.BundleFlag.GET_BUNDLE_INFO_OF_ALL_DEVICE_MODE;

try {
  bundleManager.getAllBundleInfoInstances(bundleName, bundleFlags).then((res: Array<bundleManager.BundleInfo>) => {
    let index = 0;
    for (let item of res) {
      hilog.info(0x0000, 'testTag', 'getAllBundleInfoInstances res: BundleInfo[%{public}d] = %{public}s', index++,
        JSON.stringify(item));
    }
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleInfoInstances failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfoInstances failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
