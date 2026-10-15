# HapModuleInfo

```TypeScript
export interface HapModuleInfo
```

The HapModuleInfo module provides information about an HAP module. Unless otherwise specified, the information is obtained through [bundle.getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md).

> **NOTE:** 
> 
> This module is no longer maintained since API version 9. You are advised to use
> [bundleManager-HapModuleInfo](arkts-ability-hapmoduleinfo-depr-i.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [HapModuleInfo](arkts-ability-hapmoduleinfo-depr-i.md)

<!--Device-unnamed-export interface HapModuleInfo--><!--Device-unnamed-export interface HapModuleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## abilityInfo

```TypeScript
readonly abilityInfo: Array<AbilityInfo>
```

Ability information.

**Type:** Array&lt;[AbilityInfo](arkts-ability-abilityinfo-depr-i.md)&gt;

**Default:** Obtains configuration information about ability

**Since:** 7

**Deprecated since:** 9

**Substitutes:** abilitiesInfo

<!--Device-HapModuleInfo-readonly abilityInfo: Array<AbilityInfo>--><!--Device-HapModuleInfo-readonly abilityInfo: Array<AbilityInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## backgroundImg

```TypeScript
readonly backgroundImg: string
```

Module background image.

**Type:** string

**Default:** Indicates the background img of this hapmodule

**Since:** 7

**Deprecated since:** 9

<!--Device-HapModuleInfo-readonly backgroundImg: string--><!--Device-HapModuleInfo-readonly backgroundImg: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## description

```TypeScript
readonly description: string
```

Module description.

**Type:** string

**Default:** Describes the hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** description

<!--Device-HapModuleInfo-readonly description: string--><!--Device-HapModuleInfo-readonly description: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## descriptionId

```TypeScript
readonly descriptionId: number
```

Module description ID.

**Type:** number

**Default:** Indicates the description of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** descriptionId

<!--Device-HapModuleInfo-readonly descriptionId: number--><!--Device-HapModuleInfo-readonly descriptionId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Device types supported by the module.

**Type:** Array&lt;string&gt;

**Default:** The device types that this hapmodule can run on

**Since:** 7

**Deprecated since:** 9

**Substitutes:** deviceTypes

<!--Device-HapModuleInfo-readonly deviceTypes: Array<string>--><!--Device-HapModuleInfo-readonly deviceTypes: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Module icon.

**Type:** string

**Default:** Indicates the icon of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** icon

<!--Device-HapModuleInfo-readonly icon: string--><!--Device-HapModuleInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

Module icon ID.

**Type:** number

**Default:** Indicates the icon id of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** iconId

<!--Device-HapModuleInfo-readonly iconId: number--><!--Device-HapModuleInfo-readonly iconId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## installationFree

```TypeScript
readonly installationFree: boolean
```

Whether installation-free is supported. **true** if supported, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether free installation of the hapmodule is supported

**Since:** 7

**Deprecated since:** 9

**Substitutes:** installationFree

<!--Device-HapModuleInfo-readonly installationFree: boolean--><!--Device-HapModuleInfo-readonly installationFree: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Module label.

**Type:** string

**Default:** Indicates the label of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** label

<!--Device-HapModuleInfo-readonly label: string--><!--Device-HapModuleInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

Module label ID.

**Type:** number

**Default:** Indicates the label id of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** labelId

<!--Device-HapModuleInfo-readonly labelId: number--><!--Device-HapModuleInfo-readonly labelId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## mainAbilityName

```TypeScript
readonly mainAbilityName: string
```

Name of the main ability.

**Type:** string

**Default:** Indicates the main ability name of this hapmodule

**Since:** 7

**Deprecated since:** 9

<!--Device-HapModuleInfo-readonly mainAbilityName: string--><!--Device-HapModuleInfo-readonly mainAbilityName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## moduleName

```TypeScript
readonly moduleName: string
```

Module name.

**Type:** string

**Default:** Indicates the name of the .hap package to which the capability belongs

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

<!--Device-HapModuleInfo-readonly moduleName: string--><!--Device-HapModuleInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
readonly name: string
```

Module name.

**Type:** string

**Default:** Indicates the name of this hapmodule

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

<!--Device-HapModuleInfo-readonly name: string--><!--Device-HapModuleInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## reqCapabilities

```TypeScript
readonly reqCapabilities: Array<string>
```

Capabilities required for module running.

**Type:** Array&lt;string&gt;

**Default:** Indicates the req capabilities of this hapmodule

**Since:** 7

**Deprecated since:** 9

<!--Device-HapModuleInfo-readonly reqCapabilities: Array<string>--><!--Device-HapModuleInfo-readonly reqCapabilities: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## supportedModes

```TypeScript
readonly supportedModes: number
```

Running modes supported by the module.

**Type:** number

**Default:** Indicates the supported modes of this hapmodule

**Since:** 7

**Deprecated since:** 9

<!--Device-HapModuleInfo-readonly supportedModes: number--><!--Device-HapModuleInfo-readonly supportedModes: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
