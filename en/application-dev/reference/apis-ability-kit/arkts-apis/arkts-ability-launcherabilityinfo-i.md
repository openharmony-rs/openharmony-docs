# LauncherAbilityInfo

```TypeScript
export interface LauncherAbilityInfo
```

The module describes the ability information of the launcher application. The information can be obtained by calling [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md) <!--Del--> or [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md) <!--DelEnd-->.

**Since:** 18

<!--Device-unnamed-export interface LauncherAbilityInfo--><!--Device-unnamed-export interface LauncherAbilityInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

Application information of the launcher ability.

**Type:** [ApplicationInfo](arkts-ability-applicationinfo-i.md)

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly applicationInfo: ApplicationInfo--><!--Device-LauncherAbilityInfo-readonly applicationInfo: ApplicationInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## elementName

```TypeScript
readonly elementName: ElementName
```

Element name of the launcher ability.

**Type:** [ElementName](arkts-ability-elementname-i.md)

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly elementName: ElementName--><!--Device-LauncherAbilityInfo-readonly elementName: ElementName-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## iconId

```TypeScript
readonly iconId: number
```

Icon ID of the launcher ability.

**Type:** number

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly iconId: long--><!--Device-LauncherAbilityInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## installTime

```TypeScript
readonly installTime: number
```

Timestamp when the launcher ability was installed, in milliseconds.

**Type:** number

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly installTime: long--><!--Device-LauncherAbilityInfo-readonly installTime: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## labelId

```TypeScript
readonly labelId: number
```

Label ID of the launcher ability.

**Type:** number

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly labelId: long--><!--Device-LauncherAbilityInfo-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## userId

```TypeScript
readonly userId: number
```

User ID of the launcher ability.

**Type:** number

**Since:** 18

<!--Device-LauncherAbilityInfo-readonly userId: int--><!--Device-LauncherAbilityInfo-readonly userId: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher
