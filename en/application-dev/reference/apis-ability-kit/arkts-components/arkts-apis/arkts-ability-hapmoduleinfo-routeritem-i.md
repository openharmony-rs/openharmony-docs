# RouterItem

Describes the router table configuration of the module.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## buildFunction

```TypeScript
readonly buildFunction: string
```

Function decorated by @Builder. The function describes the UI of the page.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## customData

```TypeScript
readonly customData: string
```

Any type of custom data in the [routing table configuration file](../../../quick-start/module-configuration-file.md#routermap), that is, JSON string of the **customData** field. You need to call **JSON.parse** to parse the field.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## data

```TypeScript
readonly data: Array<DataItem>
```

User-defined string in the [routing table configuration file](../../../quick-start/module-configuration-file.md#routermap), that is, value of the **data** field. This field is parsed by the system. You do not need to parse it.

**Type:** Array&lt;[DataItem](arkts-ability-hapmoduleinfo-dataitem-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Name of the page to be redirected to.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pageSourceFile

```TypeScript
readonly pageSourceFile: string
```

Path of the page in the module.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
