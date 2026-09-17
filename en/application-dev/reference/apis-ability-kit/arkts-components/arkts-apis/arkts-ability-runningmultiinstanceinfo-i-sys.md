# RunningMultiInstanceInfo (System API)

The module defines the information of a multi-instance application in the running state. The information can be obtained through [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md) of appManager.

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## instanceKey

```TypeScript
instanceKey: string
```

Unique instance ID of a multi-instance application.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pids

```TypeScript
pids: Array<number>
```

Process ID set of the application.

**Type:** Array&lt;number&gt;

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
