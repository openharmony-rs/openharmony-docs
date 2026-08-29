# getAllBundleResourceInfo（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getAllBundleResourceInfo

```TypeScript
function getAllBundleResourceInfo(resourceFlags: number, callback: AsyncCallback<Array<BundleResourceInfo>>): void
```

根据给定的resourceFlags获取所有应用的BundleResourceInfo。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | number | 是 | 指定返回的BundleResourceInfo所包含的信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;BundleResourceInfo&gt;&gt; | 是 | [回调函数](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为 undefined，data为获取到的BundleResourceInfo数组；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllBundleResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed: %{public}s', message);
}
```

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllBundleResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed: %{public}s', message);
}
```


## getAllBundleResourceInfo

```TypeScript
function getAllBundleResourceInfo(resourceFlags: number): Promise<Array<BundleResourceInfo>>
```

根据给定的resourceFlags获取所有应用的BundleResourceInfo。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | number | 是 | 指定返回的BundleResourceInfo所包含的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Array &lt;BundleResourceInfo&gt;&gt; | Promise对象，返回BundleResourceInfo数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例**

参见 [getAllBundleResourceInfo](#getallbundleresourceinfo)
