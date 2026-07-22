# getAbilityIcon（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void
```

通过bundleName、moduleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)，使用callback异步回调。

获取调用方信息时不需要权限。
> **说明：**  
>  
> 从API version 9开始支持，从API version 10开始废弃，建议使用  
> [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent)  
> 替代。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** getMediaContent

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void--><!--Device-bundleManager-function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| moduleName | string | 是 | 要查询的应用Module名称。 |
| abilityName | string | 是 | 要查询的Ability组件名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;image.PixelMap&gt; | 是 | 回调函数，返回指定[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)，作为程序启动时的入参。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-指定的ability被禁用) | The specified ability is disabled. |


## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string): Promise<image.PixelMap>
```

通过bundleName、moduleName和abilityName获取对应Icon的[PixelMap](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)，使用Promise异步回调。

获取调用方信息时不需要权限。
> **说明：**  
>  
> 从API version 9开始支持，从API version 10开始废弃，建议使用  
> [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getmediacontent)  
> 替代。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** getMediaContent

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundleManager-function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string): Promise<image.PixelMap>--><!--Device-bundleManager-function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| moduleName | string | 是 | 要查询的应用Module名称。 |
| abilityName | string | 是 | 要查询的Ability组件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle is not found. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified module is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified ability is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-指定的ability被禁用) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 需要替换为要查询的应用Bundle名称、Module名称和Ability组件名
let bundleName: string = "com.example.myapplication";
let moduleName: string = "entry";
let abilityName: string = "EntryAbility";

try {
  bundleManager.getAbilityIcon(bundleName, moduleName, abilityName).then((data) => {
    hilog.info(0x0000,'testTag', 'getAbilityIcon successful. Data: %{public}s',JSON.stringify(data));
  }).catch((error: BusinessError) => {
    hilog.error(0x0000,'testTag', 'getAbilityIcon failed. Cause: %{public}s',error.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityIcon failed. Cause: %{public}s', message);
}

```

