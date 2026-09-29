# ModuleAbilityInfo (System API)

```TypeScript
export interface ModuleAbilityInfo
```

ModuleAbilityInfo: the ability info of a module.

**Since:** 9

<!--Device-unnamed-export interface ModuleAbilityInfo--><!--Device-unnamed-export interface ModuleAbilityInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## exported

```TypeScript
readonly exported: boolean
```

Whether the ability can be invoked by other applications. **true** if it can be invoked by other applications, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-ModuleAbilityInfo-readonly exported: boolean--><!--Device-ModuleAbilityInfo-readonly exported: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## forms

```TypeScript
readonly forms: Array<AbilityFormInfo>
```

Widget information.

**Type:** Array&lt;[AbilityFormInfo](arkts-ability-bundlepackinfo-abilityforminfo-i-sys.md)&gt;

**Since:** 9

<!--Device-ModuleAbilityInfo-readonly forms: Array<AbilityFormInfo>--><!--Device-ModuleAbilityInfo-readonly forms: Array<AbilityFormInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## label

```TypeScript
readonly label: string
```

Name of the ability displayed to users. The value is a resource index to names in multiple languages.

**Type:** string

**Since:** 9

<!--Device-ModuleAbilityInfo-readonly label: string--><!--Device-ModuleAbilityInfo-readonly label: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Name of the ability. The name must be unique in the bundle.

**Type:** string

**Since:** 9

<!--Device-ModuleAbilityInfo-readonly name: string--><!--Device-ModuleAbilityInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
