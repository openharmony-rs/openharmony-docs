# RunningAppClone（系统接口）

定义分身应用在运行态的结构信息。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## appCloneIndex

```TypeScript
appCloneIndex: number
```

分身应用的索引，用于标识不同的分身实例。索引从0开始，按分身创建顺序递增，0表示主应用实例，1及以上表示分身实例。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pids

```TypeScript
pids: Array<number>
```

应用的进程ID集合。

**类型：** Array&lt;number&gt;

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

表示应用程序的UID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
