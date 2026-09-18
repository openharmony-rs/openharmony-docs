# ShortcutInfo


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> [bundleManager-ShortcutInfo](#shortcutinfo) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ShortcutInfo](#shortcutinfo)

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

**System capability:** SystemCapability.BundleManager.BundleFramework

## disableMessage

```TypeScript
readonly disableMessage: string
```

Message displayed when the shortcut is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 9

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

**System capability:** SystemCapability.BundleManager.BundleFramework

## isHomeShortcut

```TypeScript
readonly isHomeShortcut?: boolean
```

Whether the shortcut is static. **true** if static, **false** otherwise.

**Type:** boolean

**Default:** false

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sourceType

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

**System capability:** SystemCapability.BundleManager.BundleFramework
