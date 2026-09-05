# HapModuleInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:16:07.351Z pushedAt=2026-09-05T10:47:30.580Z -->

The module defines the HAP module information. An application can obtain its own HAP module information through [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** passed in for [bundleFlags](js-apis-bundleManager.md#bundleflag).

> **NOTE**
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## HapModuleInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name                              | Type                                                         | Read-Only | Optional | Description                |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | -------------------- |
| name                              | string                                                       | Yes  | No   | Module name.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| icon                              | string                                                       | Yes  | No   | [Icon](../../quick-start/layered-image.md) of the entry ability of the current module. The value is the index of the icon resource file, which is the same as the value of the **icon** field of the [abilities tag](../../quick-start/module-configuration-file.md#abilities-tag) or [extensionAbilities tag](../../quick-start/module-configuration-file.md#extensionabilities-tag) in the module configuration file. If no entry ability is configured, the value is empty.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| iconId                            | number                                                       | Yes  | No   | [Resource ID](../../quick-start/resource-categories-and-access.md#resource-directory) of the icon of the entry ability of the current module. If no entry ability is configured, the value is **0**.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| label                             | string                                                       | Yes  | No   | Name of the entry ability of the current module. The value is the index of the string resource, which is the same as the value of the **label** field of the [abilities tag](../../quick-start/module-configuration-file.md#abilities-tag) or [extensionAbilities tag](../../quick-start/module-configuration-file.md#extensionabilities-tag) in the module configuration file. If no entry ability is configured, the value is empty.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| labelId                           | number                                                       | Yes  | No   | [Resource ID](../../quick-start/resource-categories-and-access.md#resource-directory) of the name of the entry ability of the current module. If no entry ability is configured, the value is **0**.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| description                       | string                                                       | Yes  | No   | Module description.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| descriptionId                     | number                                                       | Yes  | No   | Resource ID of the description.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| mainElementName                   | string                                                       | Yes  | No   | Name of the entry UIAbility or ExtensionAbility of the current module.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| abilitiesInfo                     | Array\<[AbilityInfo](js-apis-bundleManager-abilityInfo.md)>         | Yes  | No   | Information about all abilities in the current module. Obtained by calling [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY** passed in as the **bundleFlags** parameter.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| extensionAbilitiesInfo            | Array\<[ExtensionAbilityInfo](js-apis-bundleManager-extensionAbilityInfo.md)> | Yes  | No   | Information about all ExtensionAbilities in the current module. Obtained by calling [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY** passed in as the **bundleFlags** parameter.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| metadata                          | Array\<[Metadata](js-apis-bundleManager-metadata.md)>               | Yes  | No   | Metadata of the current module. Obtained by calling [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_METADATA** passed in as the **bundleFlags** parameter.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| deviceTypes                       | Array\<string>                                               | Yes  | No   | Set of [device types](../../quick-start/module-configuration-file.md#devicetypes-tag) on which the module can be installed and run.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| installationFree                  | boolean                                                      | Yes  | No   | Whether the module supports installation-free (without requiring the user to explicitly install it from the app market). The value **true** indicates that installation-free is supported, and **false** indicates the opposite.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| hashValue                         | string                                                       | Yes  | No   | Hash value of the module, which uniquely identifies the module. The hash value is calculated based on the module content and can be used to verify module integrity and compare versions.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| type                              | [bundleManager.ModuleType](js-apis-bundleManager.md#moduletype)            | Yes  | No   | Identifies the type of the current module.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| preloads                          | Array\<[PreloadItem](#preloaditem)>                          | Yes  | No   | Preload list of the modules in the atomic service.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| dependencies                      | Array\<[Dependency](#dependency)>                            | Yes  | No   | List of dynamic shared libraries that the module depends on at runtime.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| fileContextMenuConfig<sup>11+</sup>     | string                                                       | Yes  | No   | File menu configuration of the module. Obtained by calling [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_MENU** passed in as the **bundleFlags** parameter.<br/>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| routerMap<sup>12+</sup>           | Array\<[RouterItem](#routeritem12)>                            | Yes  | No   | [Route table configuration of the module](../../quick-start/module-configuration-file.md#routermap-tag). Obtained by calling [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ROUTER_MAP** passed in as the **bundleFlags** parameter.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| codePath<sup>12+</sup>            | string                                                       | Yes  | No   | Installation path of the module.<br/>**Atomic service API:** Since API version 12, this API is supported in atomic services. |
| nativeLibraryPath<sup>12+</sup>     | string                                                       | Yes  | No   | Path of the local library file of the module in the application.                    |

## PreloadItem

Describes the preloaded module information in the atomic service.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name     | Type          | Read-Only| Optional| Description                       |
| --------- | -------------- | ---- | ---- | --------------------------- |
|moduleName | string         | Yes  | No  | Module name.|

## Dependency

Describes the information about the dynamic shared library on which the module depends.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name       | Type  | Read-Only| Optional| Description                  |
| ----------- | ------ | ---- | ---- | ---------------------- |
| bundleName<sup>10+</sup>  | string | Yes  | No  | Name of the shared bundle on which the current module depends.      |
| moduleName  | string | Yes  | No  | Module name of the shared bundle on which the current module depends.|
| versionCode<sup>10+</sup> | number | Yes  | No  | Version number of the shared bundle.  |

## RouterItem<sup>12+</sup>

Describes the router table configuration of the module.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name          | Type  | Read-Only| Optional| Description                  |
| ------------- | ------ | ---- | ---- | ---------------------- |
| name          | string | Yes  | No  | Name of the page to be redirected to.      |
| pageSourceFile| string | Yes  | No  | Path of the page in the module.  |
| buildFunction | string | Yes  | No  | Function decorated by @Builder. The function describes the UI of the page.  |
| data          | Array\<[DataItem](#dataitem12)> | Yes  | No  | User-defined string in the [routing table configuration file](../../quick-start/module-configuration-file.md#routermap), that is, value of the **data** field. This field is parsed by the system. You do not need to parse it.  |
| customData    | string | Yes  | No  | Any type of custom data in the [routing table configuration file](../../quick-start/module-configuration-file.md#routermap), that is, JSON string of the **customData** field. You need to call **JSON.parse** to parse the field.  |

## DataItem<sup>12+</sup>

Describes the user-defined data in the routing table configuration of the module.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name         | Type   | Read-Only| Optional| Description                  |
| ------------- | ------ | ---- | ---- | ---------------------- |
| key           | string | Yes  | No  | Key of the user-defined data.      |
| value         | string | Yes  | No  | Value of the user-defined data.|
