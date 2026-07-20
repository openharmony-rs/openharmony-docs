# getLauncherAbilityResourceInfoList（系统接口）

## 导入模块

```TypeScript
import { bundleResourceManager } from '@kit.AbilityKit';
```

<a id="getlauncherabilityresourceinfolist"></a>
## getLauncherAbilityResourceInfoList

```TypeScript
function getLauncherAbilityResourceInfoList(optionsList: Array<BundleOptions>, resourceFlags: number): Promise<Array<LauncherAbilityResourceInfo>>
```

根据传入的optionsList获取列表中每个BundleOptions元素对应的应用的LauncherAbilityResourceInfo。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleResourceManager-function getLauncherAbilityResourceInfoList(optionsList: Array<BundleOptions>, resourceFlags: int): Promise<Array<LauncherAbilityResourceInfo>>--><!--Device-bundleResourceManager-function getLauncherAbilityResourceInfoList(optionsList: Array<BundleOptions>, resourceFlags: int): Promise<Array<LauncherAbilityResourceInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optionsList | Array&lt;BundleOptions&gt; | 是 | 要查询的应用的参数列表。<br/>其中bundleName、moduleName、abilityName为必传参数。<br/>appIndex取值范围：[0, 5]，不传时默认为0。<br/>userId为无效参数，无需传入，传入不生效。 |
| resourceFlags | number | 是 | 指定返回的LauncherAbilityResourceInfo所包含的信息，取值为[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md)枚举值，不支持取值[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL和[ResourceFlag](arkts-ability-bundleresourcemanager-resourceflag-e-sys.md).GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;LauncherAbilityResourceInfo&gt;&gt; | Promise对象，返回指定应用列表的LauncherAbilityResourceInfo。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module is not existed. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not existed. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际要查询的应用的信息
let option: bundleManager.BundleOptions = {
  bundleName: 'com.example.demo',
  moduleName: 'entry',
  abilityName: 'EntryAbility',
  appIndex: 0
};

let optionsList: Array<bundleManager.BundleOptions> = [];
optionsList.push(option);
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getLauncherAbilityResourceInfoList(optionsList, resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed: %{public}s', message);
}

```

