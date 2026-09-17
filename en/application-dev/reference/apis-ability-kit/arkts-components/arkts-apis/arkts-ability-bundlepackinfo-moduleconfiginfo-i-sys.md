# ModuleConfigInfo (System API)

ModuleConfigInfo: the module summary of a bundle.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## abilities

```TypeScript
readonly abilities: Array<ModuleAbilityInfo>
```

Ability information of the module.

**Type:** Array&lt;[ModuleAbilityInfo](arkts-ability-bundlepackinfo-moduleabilityinfo-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## apiVersion

```TypeScript
readonly apiVersion: ApiVersion
```

API version of the module.

**Type:** [ApiVersion](arkts-ability-bundlepackinfo-apiversion-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Device types supported by the module.

**Type:** Array&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## distro

```TypeScript
readonly distro: ModuleDistroInfo
```

Distribution information of the module.

**Type:** [ModuleDistroInfo](arkts-ability-bundlepackinfo-moduledistroinfo-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## extensionAbilities

```TypeScript
readonly extensionAbilities: Array<ExtensionAbility>
```

ExtensionAbility information of the module.

**Type:** Array&lt;[ExtensionAbility](arkts-ability-bundlepackinfo-extensionability-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## mainAbility

```TypeScript
readonly mainAbility: string
```

Name of the main ability.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
