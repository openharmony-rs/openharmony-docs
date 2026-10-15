# Metadata

```TypeScript
export interface Metadata
```

Represents a metadata object, which can be obtained through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), where the **bundleFlags** parameter must contain at least GET_BUNDLE_INFO_WITH_METADATA. This object is included in [ApplicationInfo](arkts-ability-applicationinfo-i.md), [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md), [AbilityInfo](arkts-ability-abilityinfo-i.md), and [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md).

**Since:** 9

<!--Device-unnamed-export interface Metadata--><!--Device-unnamed-export interface Metadata-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

Metadata name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Metadata-name: string--><!--Device-Metadata-name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## resource

```TypeScript
resource: string
```

Metadata resource descriptor. For example, $profile:config_file indicates that the config_file.json file is configured in the profile directory.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Metadata-resource: string--><!--Device-Metadata-resource: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## value

```TypeScript
value: string
```

Metadata value.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Metadata-value: string--><!--Device-Metadata-value: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## valueId

```TypeScript
readonly valueId?: number
```

Metadata value ID. When valueId is not 0, the current metadata value is a custom configuration, and valueId must be used to obtain the corresponding value from the resource manager. When valueId is 0, the current metadata value is a fixed string.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-Metadata-readonly valueId?: long--><!--Device-Metadata-readonly valueId?: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
