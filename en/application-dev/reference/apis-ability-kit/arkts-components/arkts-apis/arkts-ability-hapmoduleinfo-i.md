# HapModuleInfo

```TypeScript
export interface HapModuleInfo
```

The module defines the HAP module information.

**Since:** 9

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## abilitiesInfo

```TypeScript
readonly abilitiesInfo: Array<AbilityInfo>
```

Information about all ability components of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[AbilityInfo](arkts-ability-abilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly abilitiesInfo: Array<AbilityInfo>--><!--Device-HapModuleInfo-readonly abilitiesInfo: Array<AbilityInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Installation path of the module.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HapModuleInfo-readonly codePath: string--><!--Device-HapModuleInfo-readonly codePath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## dependencies

```TypeScript
readonly dependencies: Array<Dependency>
```

Dynamic shared libraries on which the module depends.

**Type:** Array&lt;[Dependency](arkts-ability-hapmoduleinfo-dependency-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly dependencies: Array<Dependency>--><!--Device-HapModuleInfo-readonly dependencies: Array<Dependency>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Module description.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly description: string--><!--Device-HapModuleInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the module description.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly descriptionId: long--><!--Device-HapModuleInfo-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Array of [device types](../../../quick-start/module-configuration-file.md#devicetypes) that the module supports for installation and running.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly deviceTypes: Array<string>--><!--Device-HapModuleInfo-readonly deviceTypes: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilitiesInfo

```TypeScript
readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>
```

Information about all ExtensionAbility components of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>--><!--Device-HapModuleInfo-readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## fileContextMenuConfig

```TypeScript
readonly fileContextMenuConfig: string
```

File menu configuration of the module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_MENU** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly fileContextMenuConfig: string--><!--Device-HapModuleInfo-readonly fileContextMenuConfig: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## hashValue

```TypeScript
readonly hashValue: string
```

Hash value of the module.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly hashValue: string--><!--Device-HapModuleInfo-readonly hashValue: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

[Icon](../../../quick-start/layered-image.md) for the entry ability of the current module. It is the index of the icon resource file and should match the value of **icon** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) field in the module configuration file. If no entry ability is configured, this parameter is left empty.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly icon: string--><!--Device-HapModuleInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the icon for the entry ability of the current module. If no entry ability is configured, this parameter is left empty.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly iconId: long--><!--Device-HapModuleInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## installationFree

```TypeScript
readonly installationFree: boolean
```

Whether the module supports the installation-free feature. Installation-free means that the module does not need to be explicitly installed through an app market. **true** if the module supports installation-free, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly installationFree: boolean--><!--Device-HapModuleInfo-readonly installationFree: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Label of the entry ability of the current module. It is the index of a string resource and should match the value of **label** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) field in the module configuration file. If no entry ability is configured, this parameter is left empty.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly label: string--><!--Device-HapModuleInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the label for the entry ability of the current module. If no entry ability is configured, this parameter is left empty.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly labelId: long--><!--Device-HapModuleInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## mainElementName

```TypeScript
readonly mainElementName: string
```

Name of the UIAbility or ExtensionAbility that serves as the entry of the current module.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly mainElementName: string--><!--Device-HapModuleInfo-readonly mainElementName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Metadata of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly metadata: Array<Metadata>--><!--Device-HapModuleInfo-readonly metadata: Array<Metadata>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Module name.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly name: string--><!--Device-HapModuleInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Local library file path of the module in the application.

**Type:** string

**Since:** 12

<!--Device-HapModuleInfo-readonly nativeLibraryPath: string--><!--Device-HapModuleInfo-readonly nativeLibraryPath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## preloads

```TypeScript
readonly preloads: Array<PreloadItem>
```

Preloaded modules in the atomic service.

**Type:** Array&lt;[PreloadItem](arkts-ability-hapmoduleinfo-preloaditem-i.md)&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly preloads: Array<PreloadItem>--><!--Device-HapModuleInfo-readonly preloads: Array<PreloadItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

[Router table configuration of the module](../../../quick-start/module-configuration-file.md#routermap). The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ROUTER_MAP** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[RouterItem](arkts-ability-hapmoduleinfo-routeritem-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HapModuleInfo-readonly routerMap: Array<RouterItem>--><!--Device-HapModuleInfo-readonly routerMap: Array<RouterItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.ModuleType
```

Type of the module.

**Type:** [bundleManager.ModuleType](arkts-ability-bundlemanager-moduletype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-HapModuleInfo-readonly type: bundleManager.ModuleType--><!--Device-HapModuleInfo-readonly type: bundleManager.ModuleType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
