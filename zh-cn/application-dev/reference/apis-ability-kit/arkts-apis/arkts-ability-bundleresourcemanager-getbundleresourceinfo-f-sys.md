# getBundleResourceInfo（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getBundleResourceInfo

```TypeScript
function getBundleResourceInfo(bundleName: string, resourceFlags?: number): BundleResourceInfo
```

以同步方法根据给定的bundleName和resourceFlags获取当前应用的BundleResourceInfo。

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定查询应用的包名。 |
| resourceFlags | number | 否 | 指定返回的BundleResourceInfo所包含的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleResourceInfo | 返回指定应用的BundleResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

**示例**

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo.label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
let appIndex = 1;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, resourceFlag, appIndex);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo.label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```


## getBundleResourceInfo

```TypeScript
function getBundleResourceInfo(bundleName: string, resourceFlags?: number, appIndex?: number): BundleResourceInfo
```

以同步方法根据给定的bundleName、resourceFlags和appIndex获取当前应用或分身应用的BundleResourceInfo。

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定查询应用的包名。 |
| resourceFlags | number | 否 | 指定返回的BundleResourceInfo所包含的信息。 |
| appIndex | number | 否 | 指定查询应用分身的ID，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleResourceInfo | 返回指定应用的BundleResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range or not found. |

**示例**

参见 [getBundleResourceInfo](#getbundleresourceinfo)
