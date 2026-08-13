# getLauncherAbilityResourceInfo（系统接口）

## getLauncherAbilityResourceInfo

```TypeScript
function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int): Array<LauncherAbilityResourceInfo>
```

以同步方法根据给定的bundleName和resourceFlags获取当前应用的LauncherAbilityResourceInfo。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int): Array<LauncherAbilityResourceInfo>--><!--Device-bundleResourceManager-function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int): Array<LauncherAbilityResourceInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定查询应用的包名。 |
| resourceFlags | int | 否 | 指定返回的LauncherAbilityResourceInfo所包含的信息，默认值为 [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md#ResourceFlag（系统接口）).GET_RESOURCE_INFO_ALL。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LauncherAbilityResourceInfo&gt; | 返回指定应用的LauncherAbilityResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```


## getLauncherAbilityResourceInfo

```TypeScript
function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int, appIndex?: int): Array<LauncherAbilityResourceInfo>
```

以同步方法根据给定的bundleName、resourceFlags和appIndex获取当前应用或分身应用的LauncherAbilityResourceInfo。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int, appIndex?: int): Array<LauncherAbilityResourceInfo>--><!--Device-bundleResourceManager-function getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: int, appIndex?: int): Array<LauncherAbilityResourceInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定查询应用的包名。 |
| resourceFlags | int | 否 | 指定返回的LauncherAbilityResourceInfo所包含的信息，默认值为 [ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md#ResourceFlag（系统接口）).GET_RESOURCE_INFO_ALL。 |
| appIndex | int | 否 | 指定查询应用分身的ID，默认值为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LauncherAbilityResourceInfo&gt; | 返回指定应用的LauncherAbilityResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range or not found. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

## 示例

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
let appIndex = 1;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag, appIndex);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

