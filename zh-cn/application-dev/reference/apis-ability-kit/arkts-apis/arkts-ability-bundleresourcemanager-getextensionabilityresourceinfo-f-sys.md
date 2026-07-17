# getExtensionAbilityResourceInfo（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

## getExtensionAbilityResourceInfo

```TypeScript
function getExtensionAbilityResourceInfo(bundleName: string, extensionAbilityType: bundleManager.ExtensionAbilityType, resourceFlags: number, appIndex?: number): Array<LauncherAbilityResourceInfo>
```

根据应用包名、扩展组件类型、资源信息标志、应用分身ID获取应用的扩展组件资源。使用同步方式返回。

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

<!--Device-bundleResourceManager-function getExtensionAbilityResourceInfo(bundleName: string, extensionAbilityType: bundleManager.ExtensionAbilityType, resourceFlags: int, appIndex?: int): Array<LauncherAbilityResourceInfo>--><!--Device-bundleResourceManager-function getExtensionAbilityResourceInfo(bundleName: string, extensionAbilityType: bundleManager.ExtensionAbilityType, resourceFlags: int, appIndex?: int): Array<LauncherAbilityResourceInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |
| extensionAbilityType | bundleManager.ExtensionAbilityType | 是 | 应用的扩展组件类型，仅支持ExtensionAbilityType.INPUT_METHOD、ExtensionAbilityType.SHARE、ExtensionAbilityType.ACTION。 |
| resourceFlags | number | 是 | 资源信息标志，指示需要获取的资源信息的内容。 |
| appIndex | number | 否 | 应用分身的ID，默认值是0。取值范围0~5，取值为0表示主应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<LauncherAbilityResourceInfo> | 返回指定应用的扩展组件资源，包含图标和名称等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | AppIndex not in valid range or not found. |

**示例：**

```TypeScript
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let extensionAbilityType = bundleManager.ExtensionAbilityType.INPUT_METHOD;
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo =
    bundleResourceManager.getExtensionAbilityResourceInfo(bundleName, extensionAbilityType, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getExtensionAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  let code = (err as BusinessError).code;
  hilog.error(0x0000, 'testTag', 'getExtensionAbilityResourceInfo failed: %{public}d %{public}s', code, message);
}

```

