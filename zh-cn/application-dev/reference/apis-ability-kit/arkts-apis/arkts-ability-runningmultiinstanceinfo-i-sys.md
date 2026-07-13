# RunningMultiInstanceInfo（系统接口）

定义多实例应用在运行态的结构信息，通过appManager的
[getRunningMultiAppInfo](arkts-ability-getrunningmultiappinfo-f-sys.md#getrunningmultiappinfo-1)来获取。

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## instanceKey

```TypeScript
instanceKey: string
```

多实例应用的唯一实例标识。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pids

```TypeScript
pids: Array<number>
```

应用的进程ID集合。

**类型：** Array<number>

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

表示应用程序的UID。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

