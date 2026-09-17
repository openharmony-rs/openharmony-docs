# Metadata

The module defines a metadata object. An application can obtain the metadata through [bundleManager.getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md), with **GET_BUNDLE_INFO_WITH_METADATA** passed in for [bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md). This object is contained in ApplicationInfo, HapModuleInfo, AbilityInfo, and [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md).

The module provides the configuration about the module, UIAbility, and ExtensionAbility. The value is of the array type. The configuration is valid only for the current module, UIAbility, or ExtensionAbility.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

Indicates the metadata name

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## resource

```TypeScript
resource: string
```

Indicates the metadata resource

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## value

```TypeScript
value: string
```

Indicates the metadata value

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## valueId

```TypeScript
readonly valueId?: number
```

Indicates the value id of the metadata

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
