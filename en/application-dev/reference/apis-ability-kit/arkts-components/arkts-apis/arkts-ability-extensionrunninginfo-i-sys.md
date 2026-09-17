# ExtensionRunningInfo (System API)

The ExtensionRunningInfo module encapsulates ExtensionAbility running information, which can be obtained through [getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## clientPackage

```TypeScript
clientPackage: Array<String>
```

Names of all packages in the process.

**Type:** Array&lt;String&gt;

**Default:** All package names under the current process

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## extension

```TypeScript
extension: ElementName
```

ExtensionAbility information.

**Type:** [ElementName](arkts-ability-elementname-i.md)

**Default:** Indicates the extension of the extension info

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Default:** process id

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## processName

```TypeScript
processName: string
```

Process name.

**Type:** string

**Default:** the name of the process

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## startTime

```TypeScript
startTime: number
```

Timestamp when the ExtensionAbility is started.

**Type:** number

**Default:** ability start time

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## type

```TypeScript
type: bundle.ExtensionAbilityType
```

ExtensionAbility type.

**Type:** [bundle.ExtensionAbilityType](arkts-ability-bundlemanager-extensionabilitytype-e.md)

**Default:** Enumerates types of the extension info

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Default:** user id

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
