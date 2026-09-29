# ShortcutWant

```TypeScript
export interface ShortcutWant
```

Describes a collection of target [Wants](../../../quick-start/module-configuration-file.md#wants) information defined within a shortcut.

**Since:** 20

<!--Device-unnamed-export interface ShortcutWant--><!--Device-unnamed-export interface ShortcutWant-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## parameters

```TypeScript
parameters?: Array<ParameterItem>
```

Custom data for launching the shortcut. The data must be strings. Both keys and values can be strings up to 1024 characters long.

**Type:** Array&lt;[ParameterItem](arkts-ability-shortcutinfo-parameteritem-i.md)&gt;

**Since:** 20

<!--Device-ShortcutWant-parameters?: Array<ParameterItem>--><!--Device-ShortcutWant-parameters?: Array<ParameterItem>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## targetAbility

```TypeScript
targetAbility: string
```

Target ability name of the shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutWant-targetAbility: string--><!--Device-ShortcutWant-targetAbility: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## targetBundle

```TypeScript
targetBundle: string
```

Target bundle name of the shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutWant-targetBundle: string--><!--Device-ShortcutWant-targetBundle: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## targetModule

```TypeScript
targetModule?: string
```

Target module name of the shortcut.

**Type:** string

**Since:** 20

<!--Device-ShortcutWant-targetModule?: string--><!--Device-ShortcutWant-targetModule?: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher
