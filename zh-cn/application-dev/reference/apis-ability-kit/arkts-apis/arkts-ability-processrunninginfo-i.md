# ProcessRunningInfo

运行进程信息，可以通过appManager中 [getProcessRunningInfos](arkts-ability-appmanager-getprocessrunninginfos-depr-f.md#getprocessrunninginfos)方法来获取运行进程信息。

> **说明：**
> 
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API version 8开始支持，从API version 9开始废弃。建议使用ProcessInformation替代。
## 导入模块  
```ts
import appManager from '@ohos.application.appManager';
```

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [ProcessInformation/ProcessInformation](arkts-ability-processinformation-i.md)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## bundleNames

```TypeScript
bundleNames: Array<string>
```

进程中所有运行的Bundle名称。

**类型：** Array&lt;string&gt;

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bundleNames](arkts-ability-processinformation-i.md#bundlenames)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [pid](arkts-ability-processinformation-i.md#pid)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## processName

```TypeScript
processName: string
```

进程名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [processName](arkts-ability-processinformation-i.md#processname)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## uid

```TypeScript
uid: number
```

应用程序的UID。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [uid](arkts-ability-processinformation-i.md#uid)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission
