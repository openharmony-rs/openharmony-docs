# ProcessRunningInfo

```TypeScript
export interface ProcessRunningInfo
```

The module defines the running information of a process. The information can be obtained through [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md) of appManager.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ProcessInformation/ProcessInformation](arkts-ability-processinformation-i.md)

<!--Device-unnamed-export interface ProcessRunningInfo--><!--Device-unnamed-export interface ProcessRunningInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## bundleNames

```TypeScript
bundleNames: Array<string>
```

Names of all running bundles in the process.

**Type:** Array&lt;string&gt;

**Default:** an array of the bundleNames running in the process

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [bundleNames](arkts-ability-processinformation-i.md#bundlenames)

<!--Device-ProcessRunningInfo-bundleNames: Array<string>--><!--Device-ProcessRunningInfo-bundleNames: Array<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Default:** process id

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [pid](arkts-ability-processinformation-i.md#pid)

<!--Device-ProcessRunningInfo-pid: number--><!--Device-ProcessRunningInfo-pid: number-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## processName

```TypeScript
processName: string
```

Process name.

**Type:** string

**Default:** the name of the process

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [processName](arkts-ability-processinformation-i.md#processname)

<!--Device-ProcessRunningInfo-processName: string--><!--Device-ProcessRunningInfo-processName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Default:** user id

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [uid](arkts-ability-processinformation-i.md#uid)

<!--Device-ProcessRunningInfo-uid: number--><!--Device-ProcessRunningInfo-uid: number-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission
