# ShortcutInfo

```TypeScript
export interface ShortcutInfo
```

The module defines shortcut information configured in the configuration file. For the [FA model](../../../application-models/ability-terminology.md#fa-model), the information is configured in the [config.json](../../../quick-start/application-configuration-file-overview-fa.md) file. For the [stage model](../../../application-models/ability-terminology.md#stage-model), the information is configured in the configuration file under **resources/base/profile** in the development view.

> **NOTE:** 
> 
> This module is no longer maintained since API version 9. You are advised to use
> [bundleManager-ShortcutInfo](arkts-ability-shortcutinfo.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ShortcutInfo](arkts-ability-shortcutinfo-depr-i.md)

<!--Device-unnamed-export interface ShortcutInfo--><!--Device-unnamed-export interface ShortcutInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
readonly bundleName: string
```

Name of the bundle that contains the shortcut.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bundleName

<!--Device-ShortcutInfo-readonly bundleName: string--><!--Device-ShortcutInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## disableMessage

```TypeScript
readonly disableMessage: string
```

Message displayed when the shortcut is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 9

<!--Device-ShortcutInfo-readonly disableMessage: string--><!--Device-ShortcutInfo-readonly disableMessage: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## hostAbility

```TypeScript
readonly hostAbility: string
```

Local ability information of the shortcut.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** hostAbility

<!--Device-ShortcutInfo-readonly hostAbility: string--><!--Device-ShortcutInfo-readonly hostAbility: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

Icon of the shortcut.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** icon

<!--Device-ShortcutInfo-readonly icon: string--><!--Device-ShortcutInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

Icon ID of the shortcut.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** iconId

<!--Device-ShortcutInfo-readonly iconId: number--><!--Device-ShortcutInfo-readonly iconId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## id

```TypeScript
readonly id: string
```

ID of the application to which the shortcut belongs.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** id

<!--Device-ShortcutInfo-readonly id: string--><!--Device-ShortcutInfo-readonly id: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## isEnabled

```TypeScript
readonly isEnabled?: boolean
```

Whether the shortcut is enabled. **true** if enabled, **false** otherwise.

**Type:** boolean

**Default:** false

**Since:** 7

**Deprecated since:** 9

**Substitutes:** visible

<!--Device-ShortcutInfo-readonly isEnabled?: boolean--><!--Device-ShortcutInfo-readonly isEnabled?: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## isHomeShortcut

```TypeScript
readonly isHomeShortcut?: boolean
```

Whether the shortcut is a home shortcut. **true** if the shortcut is a home shortcut, **false** otherwise.

**Type:** boolean

**Default:** false

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sourceType

<!--Device-ShortcutInfo-readonly isHomeShortcut?: boolean--><!--Device-ShortcutInfo-readonly isHomeShortcut?: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## isStatic

```TypeScript
readonly isStatic?: boolean
```

Whether the shortcut is static. **true** if static, **false** otherwise.

**Type:** boolean

**Default:** false

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sourceType

<!--Device-ShortcutInfo-readonly isStatic?: boolean--><!--Device-ShortcutInfo-readonly isStatic?: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

Name of the shortcut.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** label

<!--Device-ShortcutInfo-readonly label: string--><!--Device-ShortcutInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

Name ID of the shortcut.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** labelId

<!--Device-ShortcutInfo-readonly labelId: number--><!--Device-ShortcutInfo-readonly labelId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## wants

```TypeScript
readonly wants: Array<ShortcutWant>
```

Want list for the shortcut.

**Type:** Array&lt;[ShortcutWant](arkts-ability-shortcutinfo-shortcutwant-depr-i-sys.md)&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** wants

<!--Device-ShortcutInfo-readonly wants: Array<ShortcutWant>--><!--Device-ShortcutInfo-readonly wants: Array<ShortcutWant>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
