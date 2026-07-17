# ExtensionRunningInfo（系统接口）

ExtensionRunningInfo模块封装了Extension运行的相关信息，可以通过[getExtensionRunningInfos接口](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md#getextensionrunninginfos-2)获取。

**起始版本：** 9

<!--Device-unnamed-export interface ExtensionRunningInfo--><!--Device-unnamed-export interface ExtensionRunningInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## clientPackage

```TypeScript
clientPackage: Array<String>
```

表示当期进程下的所有包名。

**类型：** Array<String>

**默认值：** All package names under the current process

**起始版本：** 9

<!--Device-ExtensionRunningInfo-clientPackage: Array<String>--><!--Device-ExtensionRunningInfo-clientPackage: Array<String>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## extension

```TypeScript
extension: ElementName
```

Extension信息。

**类型：** ElementName

**默认值：** Indicates the extension of the extension info

**起始版本：** 9

<!--Device-ExtensionRunningInfo-extension: ElementName--><!--Device-ExtensionRunningInfo-extension: ElementName-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pid

```TypeScript
pid: number
```

进程ID。

**类型：** number

**默认值：** process id

**起始版本：** 9

<!--Device-ExtensionRunningInfo-pid: int--><!--Device-ExtensionRunningInfo-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## processName

```TypeScript
processName: string
```

进程名称。

**类型：** string

**默认值：** the name of the process

**起始版本：** 9

<!--Device-ExtensionRunningInfo-processName: string--><!--Device-ExtensionRunningInfo-processName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## startTime

```TypeScript
startTime: number
```

Extension被启动时的时间戳。

**类型：** number

**默认值：** ability start time

**起始版本：** 9

<!--Device-ExtensionRunningInfo-startTime: long--><!--Device-ExtensionRunningInfo-startTime: long-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: bundle.ExtensionAbilityType
```

Extension类型。

**类型：** bundle.ExtensionAbilityType

**默认值：** Enumerates types of the extension info

**起始版本：** 9

<!--Device-ExtensionRunningInfo-type: bundle.ExtensionAbilityType--><!--Device-ExtensionRunningInfo-type: bundle.ExtensionAbilityType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

应用程序的uid。

**类型：** number

**默认值：** user id

**起始版本：** 9

<!--Device-ExtensionRunningInfo-uid: int--><!--Device-ExtensionRunningInfo-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

