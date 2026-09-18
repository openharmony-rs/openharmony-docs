# ShortcutInfo

Describes the configuration information for a shortcut.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone to which the shortcut belongs.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application to which the shortcut belongs.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## hostAbility

```TypeScript
hostAbility?: string
```

Name of the ability that hosts the shortcut.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## icon

```TypeScript
icon?: string
```

Icon of the shortcut. The value is the index of a resource file.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## iconId

```TypeScript
iconId?: number
```

Resource ID of the shortcut icon.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## id

```TypeScript
id: string
```

ID of the shortcut.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## label

```TypeScript
label?: string
```

Label of the shortcut. The value can be descriptive text or a resource index.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## labelId

```TypeScript
labelId?: number
```

Resource ID of the shortcut label.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## moduleName

```TypeScript
moduleName?: string
```

Module name of the shortcut.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## sourceType

```TypeScript
sourceType: number
```

Source type of the shortcut. The value **0** means a custom shortcut, **1** means a static shortcut, and **2** means a dynamic shortcut. Dynamic shortcuts are supported since API version 23.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## visible

```TypeScript
visible?: boolean
```

Whether the shortcut is visible. **true** if visible, **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## wants

```TypeScript
wants?: Array<ShortcutWant>
```

A collection of target Wants information defined within the shortcut.

**Type:** Array&lt;[ShortcutWant](arkts-ability-shortcutinfo-shortcutwant-i.md)&gt;

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher
