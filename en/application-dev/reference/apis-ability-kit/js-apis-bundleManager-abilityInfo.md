# AbilityInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:09:10.499Z pushedAt=2026-09-05T10:47:30.552Z -->

The module defines the ability information. An application can obtain its own ability information through [bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY** passed in to [bundleFlags](js-apis-bundleManager.md#bundleflag).

> **NOTE**
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## AbilityInfo

 **System capability**: SystemCapability.BundleManager.BundleFramework.Core

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name                 | Type                                                    | Read-Only| Optional| Description                                     |
| --------------------- | -------------------------------------------------------- | ---- | ---- | ------------------------------------------ |
| bundleName            | string                                                   | Yes  | No  | Bundle name.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| moduleName            | string                                                   | Yes  | No  | Module name to which the ability belongs.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| name                  | string                                                   | Yes  | No   | Ability name, corresponding to the name field configured under abilities in [module.json5](../../quick-start/module-configuration-file.md).<br>**Atomic service API:** This API supports use in atomic services since API version 11. |
| label                 | string                                                   | Yes  | No  | Resource descriptor of the ability name visible to users. It corresponds to the **label** field under **abilities** in the [module.json5](../../quick-start/module-configuration-file.md) file.<br>Note: Starting from API version 20, if [bundleManager.getAbilityInfo](js-apis-bundleManager.md#bundlemanagergetabilityinfo20) is used to obtain ability information, this field is the ability name visible to users.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| labelId               | number                                                   | Yes  | No  | Resource ID of the ability label. It is automatically generated during compilation and build based on the label configured in **abilities** of the application.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| description           | string                                                   | Yes  | No  | Ability description, which describes the content and functions of the current ability. It corresponds to the **description** field under **abilities** in the [module.json5](../../quick-start/module-configuration-file.md) file.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| descriptionId         | number                                                   | Yes  | No   | Description resource ID of the ability, automatically generated during compilation based on the description configured under abilities in the application configuration.<br>**Atomic service API:** This API supports use in atomic services since API version 11. |
| icon                  | string                                                   | Yes  | No  | Resource descriptor of the ability icon. It corresponds to the **icon** field under **abilities** in the [module.json5](../../quick-start/module-configuration-file.md) file.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| iconId                | number                                                   | Yes  | No  | Resource ID of the ability icon. It is automatically generated during compilation and build based on the icon configured in **abilities** of the application.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| process               | string                                                   | Yes  | No  | Process name of the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| exported             | boolean                                                  | Yes  | No  | Whether the ability can be launched by other applications. **true** if the ability can be launched by other applications, **false** otherwise.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| type                  | [bundleManager.AbilityType](js-apis-bundleManager.md#abilitytype)      | Yes  | No  | Ability type.<br>**Model restriction**: This API can be used only in the FA model.|
| orientation           | [bundleManager.DisplayOrientation](js-apis-bundleManager.md#displayorientation)  | Yes  | No   | Display mode of the ability. Derived from the orientation field configured under the abilities tag in [module.json5](../../quick-start/module-configuration-file.md). If the orientation configured in the module.json5 configuration file is an enum, the orientation attribute has a non-zero value. For details about the value, see [DisplayOrientation](js-apis-bundleManager.md#displayorientation). If a resource index is configured in the configuration file, the orientation attribute value is 0.<br>**Atomic service API:** This API supports use in atomic services since API version 11. |
| launchType            | [bundleManager.LaunchType](js-apis-bundleManager.md#launchtype)        | Yes  | No   | Launch mode of the ability, indicating whether to start with multiple instances at startup. For details, see [LaunchType](js-apis-bundleManager.md#launchtype).<br>**Atomic service API:** This API supports use in atomic services since API version 11. |
| permissions           | Array\<string>                                           | Yes  | No  | Array of permissions that other applications must request to start or access this ability. The system checks whether the caller has these permissions only if the **exported** property in **AbilityInfo** is **true** (meaning that the ability allows itself to be started by other applications).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| readPermission        | string                                                   | Yes  | No  | Permission required for reading the ability data.<br>**Model restriction**: This API can be used only in the FA model.|
| writePermission       | string                                                   | Yes  | No  | Permission required for writing data to the ability.<br>**Model restriction**: This API can be used only in the FA model.|
| uri                   | string                                                   | Yes  | No  | URI of the ability.<br>**Model restriction**: This API can be used only in the FA model.|
| deviceTypes           | Array\<string>                                           | Yes  | No  | Device types supported by the ability. The value is derived from that of [deviceTypes](../../quick-start/module-configuration-file.md#devicetypes) in the **module.json5** file.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| applicationInfo       | [ApplicationInfo](js-apis-bundleManager-applicationInfo.md)     | Yes  | No  |Application configuration information <!--Del-->. The information can be obtained by passing in **GET_ABILITY_INFO_WITH_APPLICATION** to the **abilityFlags** parameter of [queryAbilityInfo](js-apis-bundleManager-sys.md#bundlemanagerqueryabilityinfo) <!--DelEnd-->.<br>This field is not returned when the [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) or [getBundleInfo](js-apis-bundleManager.md#bundlemanagergetbundleinfo14) is used to obtain ability information. You can obtain the related information by obtaining the [bundleInfo](js-apis-bundleManager-bundleInfo.md#bundleinfo-1).appInfo object.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| metadata              | Array\<[Metadata](js-apis-bundleManager-metadata.md)>           | Yes  | No  | Metadata of the ability. You can configure the system-defined parameters to use the capabilities provided by the system, for example, [shortcuts](../../quick-start/module-configuration-file.md#shortcuts) and [window metadata configuration](../../windowmanager/window-config-m.md). You can also customize the parameters and call [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) to obtain the parameters by passing **GET_BUNDLE_INFO_WITH_HAP_MODULE**, **GET_BUNDLE_INFO_WITH_ABILITY**, and **GET_BUNDLE_INFO_WITH_METADATA** to **bundleFlags**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| enabled               | boolean                                                  | Yes  | No  | Whether the ability is available, that is, whether it can be started or queried. **true** if available, **false** otherwise. If the ability is unavailable, you must call [getAbilityInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetabilityinfo20) with **AbilityFlag** set to **GET_ABILITY_INFO_WITH_DISABLE** to query the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| supportWindowModes    | Array\<[bundleManager.SupportWindowMode](js-apis-bundleManager.md#supportwindowmode)> | Yes  | No  | Window modes supported by the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| windowSize|[WindowSize](#windowsize)                                            |    Yes  | No  | Window size.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| excludeFromDock<sup>12+</sup>             | boolean                                                  | Yes  | No  | Whether the ability icon can be hidden in the dock area. **true** if the ability icon can be hidden in the dock area, **false** otherwise.<br>Note: This field does not take effect.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| skills<sup>12+</sup>             | Array\<[Skill](js-apis-bundleManager-skill.md)>                                                 | Yes  | No  | Skills information of the ability. It represents the feature set of [wants](../../application-models/want-overview.md) that can be received by the UIAbility or ExtensionAbility.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| appIndex<sup>12+</sup>    | number    | Yes  | No   | Clone index identifier of the application package. The value is a natural number, where 0 indicates the primary application and a value greater than 0 indicates a clone application. This field takes effect only in [app clone](../../quick-start/app-clone.md). |
| orientationId<sup>14+</sup>    | number      | Yes  | No  | Resource ID of the ability display mode. It is derived from the **orientation** field under **abilities** in the [module.json5](../../quick-start/module-configuration-file.md) file. If the **orientation** field in the file is set to an enumerated value, **orientationId** is **0**. If the **orientation** field is set to a resource index, **orientationId** is a non-zero value, which is the resource ID generated during building. If **orientationId** is set to a value other than **0**, the current display mode is customized, and this ID must be used to obtain the corresponding resource from the resource manager module. If **orientationId** is set to **0**, no resource is configured.<br>**Atomic service API**: This API can be used in atomic services since API version 14.|

## WindowSize

Describes the window size.

 <br>**Atomic service API**: This API can be used in atomic services since API version 11.

 **System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name              | Type   | Read-Only| Optional| Description                              |
| -------------------| ------- | ---- | ---- | ---------------------------------- |
| maxWindowRatio     | number  | Yes   | No   | Indicates the maximum aspect ratio (width/height) of the window in free-form window state.<br>Value range: [0, 1]. For example, 0.62 indicates that the maximum window width is 0.62 times the height. This attribute is used to limit the display ratio of the window. |
| minWindowRatio     | number  | Yes   | No   | Indicates the minimum aspect ratio (width/height) of the window in free-form window state.<br>Value range: [0, 1]. For example, 0.12 indicates that the minimum window width is 0.12 times the height. This attribute is used to limit the display ratio of the window. |
| maxWindowWidth     | number  | Yes  | No  | Maximum width of the window in free window mode. The unit is vp.|
| minWindowWidth     | number  | Yes  | No  | Minimum width of the window in free window mode. The unit is vp.|
| maxWindowHeight    | number  | Yes  | No  | Maximum height of the window in free window mode. The unit is vp.|
| minWindowHeight    | number  | Yes  | No  | Minimum height of the window in free window mode. The unit is vp.|