# ShortcutInfo

```TypeScript
export interface ShortcutInfo
```

The module describes the shortcut information defined in the [module.json5](../../../quick-start/module-configuration-file.md#shortcuts) file of an application. The information can be obtained by running [getAllShortcutInfoForSelf](arkts-ability-shortcutmanager-getallshortcutinfoforself-f.md)<!--Del--> or [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md)<!--DelEnd-->.

**Since:** 20

<!--Device-unnamed-export interface ShortcutInfo--><!--Device-unnamed-export interface ShortcutInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone to which the shortcut belongs.

**Type:** number

**Since:** 20

<!--Device-ShortcutInfo-appIndex: int--><!--Device-ShortcutInfo-appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application to which the shortcut belongs.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-bundleName: string--><!--Device-ShortcutInfo-bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## hostAbility

```TypeScript
hostAbility?: string
```

Name of the host ability of the shortcut, that is, the name of the ability that carries this shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-hostAbility?: string--><!--Device-ShortcutInfo-hostAbility?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## icon

```TypeScript
icon?: string
```

Icon of the shortcut. The value is the index of a resource file.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-icon?: string--><!--Device-ShortcutInfo-icon?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## iconId

```TypeScript
iconId?: number
```

Resource ID of the shortcut icon.

**Type:** number

**Since:** 20

<!--Device-ShortcutInfo-iconId?: long--><!--Device-ShortcutInfo-iconId?: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## id

```TypeScript
id: string
```

ID of the shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-id: string--><!--Device-ShortcutInfo-id: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## label

```TypeScript
label?: string
```

Label of the shortcut. The value can be descriptive text or a resource index.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-label?: string--><!--Device-ShortcutInfo-label?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## labelId

```TypeScript
labelId?: number
```

Resource ID of the shortcut label.

**Type:** number

**Since:** 20

<!--Device-ShortcutInfo-labelId?: long--><!--Device-ShortcutInfo-labelId?: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## moduleName

```TypeScript
moduleName?: string
```

Module name of the shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutInfo-moduleName?: string--><!--Device-ShortcutInfo-moduleName?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## sourceType

```TypeScript
sourceType: number
```

Source type of the shortcut. The value **0** means a custom shortcut, **1** means a static shortcut, and **2** means a dynamic shortcut. Dynamic shortcuts are supported since API version 23.

**Type:** number

**Since:** 20

<!--Device-ShortcutInfo-sourceType: int--><!--Device-ShortcutInfo-sourceType: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## visible

```TypeScript
visible?: boolean
```

Whether the shortcut is visible. **true** if visible, **false** otherwise. The default value is **true**.

**Type:** boolean

**Since:** 20

<!--Device-ShortcutInfo-visible?: boolean--><!--Device-ShortcutInfo-visible?: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## wants

```TypeScript
wants?: Array<ShortcutWant>
```

A collection of target Wants information defined within the shortcut.

**Type:** Array&lt;[ShortcutWant](arkts-ability-shortcutinfo-shortcutwant-i.md)&gt;

**Since:** 20

<!--Device-ShortcutInfo-wants?: Array<ShortcutWant>--><!--Device-ShortcutInfo-wants?: Array<ShortcutWant>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher
