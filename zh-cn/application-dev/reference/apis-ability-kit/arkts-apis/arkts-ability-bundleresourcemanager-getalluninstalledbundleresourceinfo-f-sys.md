# getAllUninstalledBundleResourceInfo（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getAllUninstalledBundleResourceInfo

```TypeScript
function getAllUninstalledBundleResourceInfo(resourceFlags: number): Promise<Array<BundleResourceInfo>>
```

根据给定的resourceFlags获取所有已卸载且保留数据的应用的BundleResourceInfo。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getAllUninstalledBundleResourceInfo(resourceFlags: int): Promise<Array<BundleResourceInfo>>--><!--Device-bundleResourceManager-function getAllUninstalledBundleResourceInfo(resourceFlags: int): Promise<Array<BundleResourceInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | number | 是 | 指定返回的BundleResourceInfo所包含的信息，取值请参考[ResourceFlag枚举值](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleResourceInfo&gt;&gt; | Promise对象，返回BundleResourceInfo数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllUninstalledBundleResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo failed: %{public}s', message);
}

```

