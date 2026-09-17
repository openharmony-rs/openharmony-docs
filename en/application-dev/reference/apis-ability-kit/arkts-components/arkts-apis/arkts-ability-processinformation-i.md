# ProcessInformation

The module defines the process information. The information can be obtained through [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md) of appManager.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## appCloneIndex

```TypeScript
appCloneIndex?: number
```

Index of an application clone.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleNames

```TypeScript
bundleNames: Array<string>
```

Names of all running bundles in the process.

**Type:** Array&lt;string&gt;

**Default:** an array of the bundleNames running in the process

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleType

```TypeScript
bundleType: bundleManager.BundleType
```

Type of the bundle running in the process.

**Type:** [bundleManager.BundleType](arkts-ability-bundlemanager-bundletype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isPreload

```TypeScript
isPreload?: boolean
```

Indicates whether the process is in the preload state.

- `true`: The process is currently in the preload state.  
- `false`: The process is either not a preload process, or its preload state has been consumed.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Default:** process id

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

Process name.

**Type:** string

**Default:** the name of the process

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: appManager.ProcessState
```

Running status of the process.

**Type:** [appManager.ProcessState](arkts-ability-appmanager-processstate-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Default:** user id

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
