# RouterItem

```TypeScript
export interface RouterItem
```

Describes the router table configuration of the module.

**Since:** 12

<!--Device-unnamed-export interface RouterItem--><!--Device-unnamed-export interface RouterItem-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## buildFunction

```TypeScript
readonly buildFunction: string
```

Function decorated by @Builder. The function describes the UI of the page.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RouterItem-readonly buildFunction: string--><!--Device-RouterItem-readonly buildFunction: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## customData

```TypeScript
readonly customData: string
```

Any type of custom data in the [routing table configuration file](../../../quick-start/module-configuration-file.md#routermap), that is, JSON string of the **customData** field. You need to call **JSON.parse** to parse the field.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RouterItem-readonly customData: string--><!--Device-RouterItem-readonly customData: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## data

```TypeScript
readonly data: Array<DataItem>
```

User-defined string in the [routing table configuration file](../../../quick-start/module-configuration-file.md#routermap), that is, value of the **data** field. This field is parsed by the system. You do not need to parse it.

**Type:** Array&lt;[DataItem](arkts-ability-hapmoduleinfo-dataitem-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RouterItem-readonly data: Array<DataItem>--><!--Device-RouterItem-readonly data: Array<DataItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
readonly name: string
```

Name of the page to be redirected to.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RouterItem-readonly name: string--><!--Device-RouterItem-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## pageSourceFile

```TypeScript
readonly pageSourceFile: string
```

Path of the page in the module.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RouterItem-readonly pageSourceFile: string--><!--Device-RouterItem-readonly pageSourceFile: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
