# AbilityRunningInfo

AbilityRunningInfo是记录Ability运行信息和状态的数据结构，通过
[getAbilityRunningInfos](arkts-ability-getabilityrunninginfos-f.md#getabilityrunninginfos-1)方法获取。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ability

```TypeScript
ability: ElementName
```

Ability的ElementName信息。

**类型：** ElementName

**默认值：** the ohos.bundleManager.ElementName object of the ability.

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## abilityState

```TypeScript
abilityState: abilityManager.AbilityState
```

Ability的状态。

**类型：** abilityManager.AbilityState

**默认值：** Enumerates state of the ability state info

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**默认值：** process id

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## processName

```TypeScript
processName: string
```

进程的名称。

**类型：** string

**默认值：** the name of the process

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## startTime

```TypeScript
startTime: number
```

Ability的启动时间。

**类型：** number

**默认值：** ability start time

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

所属应用程序的UID。

**类型：** number

**默认值：** user id

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

