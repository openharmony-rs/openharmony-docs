# ApplicationQuickFixInfo (System API)

Defines the quick fix information at the application level.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## bundleVersionCode

```TypeScript
readonly bundleVersionCode: number
```

Internal version number of the application.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## bundleVersionName

```TypeScript
readonly bundleVersionName: string
```

Version number of the application that is shown to users.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## hapModuleQuickFixInfo

```TypeScript
readonly hapModuleQuickFixInfo: Array<HapModuleQuickFixInfo>
```

Quick fix information at the HAP file level.

**Type:** Array&lt;[HapModuleQuickFixInfo](arkts-ability-quickfixmanager-hapmodulequickfixinfo-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## quickFixVersionCode

```TypeScript
readonly quickFixVersionCode: number
```

Version code of the quick fix patch package.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.

## quickFixVersionName

```TypeScript
readonly quickFixVersionName: string
```

Text description of the version number of the quick fix patch package.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.QuickFix

**System API:** This is a system API.
