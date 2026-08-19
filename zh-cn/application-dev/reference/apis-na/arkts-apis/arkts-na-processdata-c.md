# ProcessData

**起始版本：** -1

<!--Device-unnamed-declare class ProcessData--><!--Device-unnamed-declare class ProcessData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 23

<!--Device-ProcessData-bundleName: string--><!--Device-ProcessData-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isContinuousTask

```TypeScript
isContinuousTask: boolean
```

是否为长时任务，true表示是，false表示不是。

**类型：** boolean

**起始版本：** 23

<!--Device-ProcessData-isContinuousTask: boolean--><!--Device-ProcessData-isContinuousTask: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isKeepAlive

```TypeScript
isKeepAlive: boolean
```

是否为常驻进程，true表示是，false表示不是。

**类型：** boolean

**起始版本：** 23

<!--Device-ProcessData-isKeepAlive: boolean--><!--Device-ProcessData-isKeepAlive: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: int
```

进程ID。

**类型：** int

**起始版本：** 23

<!--Device-ProcessData-pid: int--><!--Device-ProcessData-pid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: int
```

进程的状态，取值及对应的状态为： 0 - 初始化状态，进程正在初始化， 1 - 就绪状态，进程已初始化完毕， 2 - 前台， 4 - 后台， 5 - 已终止。

**类型：** int

**起始版本：** 23

<!--Device-ProcessData-state: int--><!--Device-ProcessData-state: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: int
```

应用的uid。

**类型：** int

**起始版本：** 23

<!--Device-ProcessData-uid: int--><!--Device-ProcessData-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

