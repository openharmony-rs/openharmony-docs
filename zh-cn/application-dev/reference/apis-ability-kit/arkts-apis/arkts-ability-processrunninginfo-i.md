# ProcessRunningInfo

运行进程信息，可以通过appManager中[getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos-1)方法来获取运行进程信息。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** ProcessInformation/ProcessInformation

<!--Device-unnamed-export interface ProcessRunningInfo--><!--Device-unnamed-export interface ProcessRunningInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## bundleNames

```TypeScript
bundleNames: Array<string>
```

进程中所有运行的Bundle名称。

**类型：** Array&lt;string&gt;

**默认值：** an array of the bundleNames running in the process

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bundleNames](arkts-ability-processinformation-i.md#bundlenames)

<!--Device-ProcessRunningInfo-bundleNames: Array<string>--><!--Device-ProcessRunningInfo-bundleNames: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**默认值：** process id

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [pid](arkts-ability-processinformation-i.md#pid)

<!--Device-ProcessRunningInfo-pid: number--><!--Device-ProcessRunningInfo-pid: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## processName

```TypeScript
processName: string
```

进程名称。

**类型：** string

**默认值：** the name of the process

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [processName](arkts-ability-processinformation-i.md#processname)

<!--Device-ProcessRunningInfo-processName: string--><!--Device-ProcessRunningInfo-processName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## uid

```TypeScript
uid: number
```

应用程序的UID。

**类型：** number

**默认值：** user id

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [uid](arkts-ability-processinformation-i.md#uid)

<!--Device-ProcessRunningInfo-uid: number--><!--Device-ProcessRunningInfo-uid: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

