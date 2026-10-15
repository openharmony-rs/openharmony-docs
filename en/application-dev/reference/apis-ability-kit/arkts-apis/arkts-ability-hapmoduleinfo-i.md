# HapModuleInfo

```TypeScript
export interface HapModuleInfo
```

The module defines the HAP module information. An application can obtain its own HAP module information through [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** passed in for [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md).

**Since:** 9

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## abilitiesInfo

```TypeScript
readonly abilitiesInfo: Array<AbilityInfo>
```

Information about all abilities in the current module. Obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY** passed in as the **bundleFlags** parameter.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;[AbilityInfo](arkts-ability-abilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly abilitiesInfo: Array<AbilityInfo>--><!--Device-HapModuleInfo-readonly abilitiesInfo: Array<AbilityInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Installation path of the module.

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HapModuleInfo-readonly codePath: string--><!--Device-HapModuleInfo-readonly codePath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## dependencies

```TypeScript
readonly dependencies: Array<Dependency>
```

List of dynamic shared libraries that the module depends on at runtime.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;[Dependency](arkts-ability-hapmoduleinfo-dependency-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly dependencies: Array<Dependency>--><!--Device-HapModuleInfo-readonly dependencies: Array<Dependency>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Module description.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly description: string--><!--Device-HapModuleInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the description.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly descriptionId: long--><!--Device-HapModuleInfo-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Set of [device types](../../../quick-start/module-configuration-file.md#devicetypes) on which the module can be installed and run.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly deviceTypes: Array<string>--><!--Device-HapModuleInfo-readonly deviceTypes: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilitiesInfo

```TypeScript
readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>
```

Information about all ExtensionAbilities in the current module. Obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY** passed in as the **bundleFlags** parameter.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;[ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>--><!--Device-HapModuleInfo-readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## fileContextMenuConfig

```TypeScript
readonly fileContextMenuConfig: string
```

File menu configuration of the module. Obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_MENU** passed in as the **bundleFlags** parameter.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly fileContextMenuConfig: string--><!--Device-HapModuleInfo-readonly fileContextMenuConfig: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## hashValue

```TypeScript
readonly hashValue: string
```

Hash value of the module, which uniquely identifies the module. The hash value is calculated based on the module content and can be used to verify module integrity and compare versions.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly hashValue: string--><!--Device-HapModuleInfo-readonly hashValue: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

[Icon](../../../quick-start/layered-image.md) of the entry ability of the current module. The value is the index of the icon resource file, which is the same as the value of the **icon** field of the [abilities tag](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities tag](../../../quick-start/module-configuration-file.md#extensionabilities) in the module configuration file. If no entry ability is configured, the value is empty.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly icon: string--><!--Device-HapModuleInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the icon of the entry ability of the current module. If no entry ability is configured, the value is **0**.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly iconId: long--><!--Device-HapModuleInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## installationFree

```TypeScript
readonly installationFree: boolean
```

Whether the module supports installation-free (without requiring the user to explicitly install it from the app market). The value **true** indicates that installation-free is supported, and **false** indicates the opposite.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly installationFree: boolean--><!--Device-HapModuleInfo-readonly installationFree: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Name of the entry ability of the current module. The value is the index of the string resource, which is the same as the value of the **label** field of the [abilities tag](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities tag](../../../quick-start/module-configuration-file.md#extensionabilities) in the module configuration file. If no entry ability is configured, the value is empty.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly label: string--><!--Device-HapModuleInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the name of the entry ability of the current module. If no entry ability is configured, the value is **0**.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly labelId: long--><!--Device-HapModuleInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## mainElementName

```TypeScript
readonly mainElementName: string
```

Name of the entry UIAbility or ExtensionAbility of the current module.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly mainElementName: string--><!--Device-HapModuleInfo-readonly mainElementName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Metadata of the current module. Obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_METADATA** passed in as the **bundleFlags** parameter.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly metadata: Array<Metadata>--><!--Device-HapModuleInfo-readonly metadata: Array<Metadata>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Module name.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly name: string--><!--Device-HapModuleInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Path of the local library file of the module in the application.

**Type:** string

**Since:** 12

<!--Device-HapModuleInfo-readonly nativeLibraryPath: string--><!--Device-HapModuleInfo-readonly nativeLibraryPath: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## preloads

```TypeScript
readonly preloads: Array<PreloadItem>
```

Preload list of the modules in the atomic service.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** Array&lt;[PreloadItem](arkts-ability-hapmoduleinfo-preloaditem-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly preloads: Array<PreloadItem>--><!--Device-HapModuleInfo-readonly preloads: Array<PreloadItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

[Route table configuration of the module](../../../quick-start/module-configuration-file.md#routermap). Obtained by calling [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md) with **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ROUTER_MAP** passed in as the **bundleFlags** parameter.

**Atomic service API:** Since API version 12, this API is supported in atomic services.

**Type:** Array&lt;[RouterItem](arkts-ability-hapmoduleinfo-routeritem-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HapModuleInfo-readonly routerMap: Array<RouterItem>--><!--Device-HapModuleInfo-readonly routerMap: Array<RouterItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.ModuleType
```

Identifies the type of the current module.

**Atomic service API:** Since API version 11, this API is supported in atomic services.

**Type:** [bundleManager.ModuleType](arkts-ability-bundlemanager-moduletype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HapModuleInfo-readonly type: bundleManager.ModuleType--><!--Device-HapModuleInfo-readonly type: bundleManager.ModuleType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
