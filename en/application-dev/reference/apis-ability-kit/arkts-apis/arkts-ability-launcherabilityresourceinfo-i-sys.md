# LauncherAbilityResourceInfo (System API)

```TypeScript
export interface LauncherAbilityResourceInfo
```

The module provides resource information of the entry ability of an application, such as the icon and label. The information can be obtained by calling [getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md).

> **NOTE:** 
> 
> The APIs provided by this module are system APIs.

**Since:** 11

<!--Device-unnamed-export interface LauncherAbilityResourceInfo--><!--Device-unnamed-export interface LauncherAbilityResourceInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## abilityName

```TypeScript
readonly abilityName: string
```

Name of the entry ability.

**Type:** string

**Since:** 11

<!--Device-LauncherAbilityResourceInfo-readonly abilityName: string--><!--Device-LauncherAbilityResourceInfo-readonly abilityName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone.

**Type:** number

**Since:** 12

<!--Device-LauncherAbilityResourceInfo-readonly appIndex: int--><!--Device-LauncherAbilityResourceInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 11

<!--Device-LauncherAbilityResourceInfo-readonly bundleName: string--><!--Device-LauncherAbilityResourceInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## drawableDescriptor

```TypeScript
readonly drawableDescriptor: DrawableDescriptor
```

**drawableDescriptor** object of the application icon.

**Type:** [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**Since:** 12

<!--Device-LauncherAbilityResourceInfo-readonly drawableDescriptor: DrawableDescriptor--><!--Device-LauncherAbilityResourceInfo-readonly drawableDescriptor: DrawableDescriptor-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## icon

```TypeScript
readonly icon: string
```

Application icon, which is encoded using Base64.

**Type:** string

**Since:** 11

<!--Device-LauncherAbilityResourceInfo-readonly icon: string--><!--Device-LauncherAbilityResourceInfo-readonly icon: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## label

```TypeScript
readonly label: string
```

Application label.

**Type:** string

**Since:** 11

<!--Device-LauncherAbilityResourceInfo-readonly label: string--><!--Device-LauncherAbilityResourceInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

## moduleName

```TypeScript
readonly moduleName: string
```

Module name of the application.

**Type:** string

**Since:** 11

<!--Device-LauncherAbilityResourceInfo-readonly moduleName: string--><!--Device-LauncherAbilityResourceInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.
