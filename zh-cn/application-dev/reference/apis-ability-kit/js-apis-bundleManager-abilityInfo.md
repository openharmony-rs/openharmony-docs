# AbilityInfo

Ability信息，可以通过[bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取Ability信息，其中参数[bundleFlags](js-apis-bundleManager.md#bundleflag)至少包含GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_ABILITY。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## AbilityInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称               | 类型                                                     | 只读 | 可选 | 说明                                      |
| ------------------ | -------------------------------------------------------- | ---- | ---- | ------------------------------------------ |
| bundleName         | string                                                   | 是   | 否   | 应用Bundle名称。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| moduleName         | string                                                   | 是   | 否   | Ability所属的模块名称。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| name               | string                                                   | 是   | 否   | Ability名称。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| label              | string                                                   | 是   | 否   | Ability对用户显示的名称的资源描述符，如："label": "$string: mainability_description"。从API version 20开始，如果是通过[bundleManager.getAbilityInfo](js-apis-bundleManager.md#bundlemanagergetabilityinfo20)获取Ability信息，该字段为Ability对用户显示的名称。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| labelId            | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | Ability的标签资源id。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| description        | string                                                   | 是   | 否   | Ability的描述。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| descriptionId      | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | Ability的描述资源id。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| icon               | string                                                   | 是   | 否   | Ability的图标资源描述符，如"icon": "$media:icon"。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| iconId             | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | Ability的图标资源id。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| process            | string                                                   | 是   | 否   | Ability的进程名称。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| exported           | boolean                                                  | 是   | 否   | 判断Ability是否可以被其他应用调用，取值为true表示Ability可以被其他应用调用，取值为false表示Ability不可以被其他应用调用。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| type               | [bundleManager.AbilityType](js-apis-bundleManager.md#abilitytype)      | 是   | 否   | Ability类型。<br>**模型约束：** 此接口仅可在FA模型下使用。<br>**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。<br>**ArkTS-Dyn起始版本：** 9 |
| orientation        | [bundleManager.DisplayOrientation](js-apis-bundleManager.md#displayorientation)  | 是   | 否   | Ability的显示模式。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| launchType         | [bundleManager.LaunchType](js-apis-bundleManager.md#launchtype)        | 是   | 否   | Ability的启动模式。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| permissions        | Array\<string>                                           | 是   | 否   | 被其他应用Ability调用时需要申请的权限集合。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| readPermission     | string                                                   | 是   | 否   | 读取Ability数据所需的权限。<br>**模型约束：** 此接口仅可在FA模型下使用。<br>**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。<br>**ArkTS-Dyn起始版本：** 9 |
| writePermission    | string                                                   | 是   | 否   | 向Ability写数据所需的权限。<br>**模型约束：** 此接口仅可在FA模型下使用。<br>**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。<br>**ArkTS-Dyn起始版本：** 9 |
| uri                | string                                                   | 是   | 否   | 获取Ability的统一资源标识符（URI）。<br />**模型约束：** 此接口仅可在FA模型下使用。<br>**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。<br>**ArkTS-Dyn起始版本：** 9 |
| deviceTypes        | Array\<string>                                           | 是   | 否   | Ability支持的设备类型。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| applicationInfo    | ArkTS-Dyn: [ApplicationInfo](js-apis-bundleManager-applicationInfo.md)<br>ArkTS-Sta: [ApplicationInfo](js-apis-bundleManager-applicationInfo.md) \| null | 是   | 否   | 应用程序的配置信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY和GET_BUNDLE_INFO_WITH_APPLICATION获取。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| metadata           | Array\<[Metadata](js-apis-bundleManager-metadata.md)>           | 是   | 否   | Ability的元信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE、GET_BUNDLE_INFO_WITH_ABILITY和GET_BUNDLE_INFO_WITH_METADATA获取。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| enabled            | boolean                                                  | 是   | 否   | Ability是否可用，取值为true表示Ability可用，取值为false表示Ability不可用。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| supportWindowModes | Array\<[bundleManager.SupportWindowMode](js-apis-bundleManager.md#supportwindowmode)> | 是   | 否   | Ability支持的窗口模式。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| windowSize|[WindowSize](#windowsize)                                            |    是   | 否   | Ability窗口尺寸。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| excludeFromDock<sup>12+</sup>             | boolean                                                  | 是   | 否   | 判断Ability是否可以在dock区域隐藏图标，取值为true表示可以隐藏，取值为false不可以隐藏。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| skills<sup>12+</sup>             | Array\<[Skill](js-apis-bundleManager-skill.md)>                                                 | 是   | 否   | Ability的Skills信息。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| appIndex<sup>12+</sup>    | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | 应用包的分身索引标识，仅在[分身应用](../../quick-start/app-clone.md)中生效。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| orientationId<sup>14+</sup>    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | Ability的显示模式资源id。当orientationId不为0时表示当前显示模式为自定义配置，需要使用orientationId去资源管理获取对应的资源，当orientationId为0时表示未配置资源。<br>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 14<br>**ArkTS-Sta起始版本：** 23 |

## WindowSize

描述窗口尺寸。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称               | 类型    | 只读 | 可选 | 说明                               |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| maxWindowRatio     | ArkTS-Dyn: number<br>ArkTS-Sta: double | 是   | 否   | 表示自由窗口状态下窗口的最大宽高比；取值范围0-1，例如：0.12。 |
| minWindowRatio     | ArkTS-Dyn: number<br>ArkTS-Sta: double | 是   | 否   | 表示自由窗口状态下窗口的最小宽高比；取值范围0-1，例如：0.5。 |
| maxWindowWidth     | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示自由窗口状态下窗口的最大宽度，宽度单位为vp。 |
| minWindowWidth     | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示自由窗口状态下窗口的最小宽度，宽度单位为vp。 |
| maxWindowHeight    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示自由窗口状态下窗口的最大高度，宽度单位为vp。 |
| minWindowHeight    | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示自由窗口状态下窗口的最小高度，宽度单位为vp。 |