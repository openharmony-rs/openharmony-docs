# RunningMultiAppInfo（系统接口）

定义应用多开在运行态的结构信息。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用的包名。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: MultiAppMode
```

应用多开模式。

**类型：** [MultiAppMode](arkts-ability-multiappmode-e-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## runningAppClones

```TypeScript
runningAppClones?: Array<RunningAppClone>
```

特定包名在运行态的分身应用信息。

**类型：** Array&lt;[RunningAppClone](arkts-ability-runningappclone-i-sys.md)&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## runningMultiInstances

```TypeScript
runningMultiInstances?: Array<RunningMultiInstanceInfo>
```

特定包名在运行态的多实例应用信息。

**类型：** Array&lt;[RunningMultiInstanceInfo](arkts-ability-runningmultiinstanceinfo-i-sys.md)&gt;

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
