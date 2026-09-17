# HapModuleInfo

The module defines the HAP module information.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## abilitiesInfo

```TypeScript
readonly abilitiesInfo: Array<AbilityInfo>
```

Information about all ability components of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ABILITY** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[AbilityInfo](arkts-ability-abilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## codePath

```TypeScript
readonly codePath: string
```

Installation path of the module.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## dependencies

```TypeScript
readonly dependencies: Array<Dependency>
```

Dynamic shared libraries on which the module depends.

**Type:** Array&lt;[Dependency](arkts-ability-hapmoduleinfo-dependency-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## description

```TypeScript
readonly description: string
```

Module description.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the module description.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Array of [device types](../../../quick-start/module-configuration-file.md#devicetypes) that the module supports for installation and running.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## extensionAbilitiesInfo

```TypeScript
readonly extensionAbilitiesInfo: Array<ExtensionAbilityInfo>
```

Information about all ExtensionAbility components of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_EXTENSION_ABILITY** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## fileContextMenuConfig

```TypeScript
readonly fileContextMenuConfig: string
```

File menu configuration of the module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_MENU** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## hashValue

```TypeScript
readonly hashValue: string
```

Hash value of the module.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## icon

```TypeScript
readonly icon: string
```

[Icon](../../../quick-start/layered-image.md) for the entry ability of the current module. It is the index of the icon resource file and should match the value of **icon** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) field in the module configuration file. If no entry ability is configured, this parameter is left empty.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the icon for the entry ability of the current module. If no entry ability is configured, this parameter is left empty.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## installationFree

```TypeScript
readonly installationFree: boolean
```

Whether the module supports the installation-free feature. Installation-free means that the module does not need to be explicitly installed through an app market. **true** if the module supports installation-free, **false** otherwise.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## label

```TypeScript
readonly label: string
```

Label of the entry ability of the current module. It is the index of a string resource and should match the value of **label** in the [abilities](../../../quick-start/module-configuration-file.md#abilities) or [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) field in the module configuration file. If no entry ability is configured, this parameter is left empty.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## labelId

```TypeScript
readonly labelId: number
```

[Resource ID](../../../quick-start/resource-categories-and-access.md#resource-directories) of the label for the entry ability of the current module. If no entry ability is configured, this parameter is left empty.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## mainElementName

```TypeScript
readonly mainElementName: string
```

Name of the UIAbility or ExtensionAbility that serves as the entry of the current module.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## metadata

```TypeScript
readonly metadata: Array<Metadata>
```

Metadata of the current module. The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_METADATA** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[Metadata](arkts-ability-metadata-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Module name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Local library file path of the module in the application.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## preloads

```TypeScript
readonly preloads: Array<PreloadItem>
```

Preloaded modules in the atomic service.

**Type:** Array&lt;[PreloadItem](arkts-ability-hapmoduleinfo-preloaditem-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## routerMap

```TypeScript
readonly routerMap: Array<RouterItem>
```

[Router table configuration of the module](../../../quick-start/module-configuration-file.md#routermap). The information can be obtained by passing in **GET_BUNDLE_INFO_WITH_HAP_MODULE** and **GET_BUNDLE_INFO_WITH_ROUTER_MAP** to the **bundleFlags** parameter of [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md).

**Type:** Array&lt;[RouterItem](arkts-ability-hapmoduleinfo-routeritem-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## type

```TypeScript
readonly type: bundleManager.ModuleType
```

Type of the module.

**Type:** [bundleManager.ModuleType](arkts-ability-bundlemanager-moduletype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
