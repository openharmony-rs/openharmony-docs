# ElementName

A structured identifier for an application component, containing fields such as **bundleName**, **moduleName**, and **abilityName**. It is usually used in [AbilityRunningInfo.ability](arkts-ability-abilityrunninginfo-i.md) for component launch information and in the [connectOptions.onConnect](arkts-ability-connectoptions-connectoptions-i.md#onconnect) callback for component connection.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## abilityName

```TypeScript
abilityName: string
```

Name of the ability.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Default:** Indicates bundle name

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## deviceId

```TypeScript
deviceId?: string
```

Device ID.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
moduleName?: string
```

Module name of the HAP file to which the ability belongs.

**Type:** string

**Default:** Indicates module name

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## shortName

```TypeScript
shortName?: string
```

Short name of the ability. It is a string starting with a period (.).

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## uri

```TypeScript
uri?: string
```

Resource ID.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
