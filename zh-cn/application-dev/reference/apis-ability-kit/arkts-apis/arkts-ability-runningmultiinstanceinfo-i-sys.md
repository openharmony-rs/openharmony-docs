# RunningMultiInstanceInfo（系统接口）

定义多实例应用在运行态的结构信息，通过appManager的 [getRunningMultiAppInfo](arkts-ability-appmanager-getrunningmultiappinfo-f-sys.md#getRunningMultiAppInfo（系统接口）)来获取。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface RunningMultiInstanceInfo--><!--Device-unnamed-export interface RunningMultiInstanceInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## instanceKey

```TypeScript
instanceKey: string
```

多实例应用的唯一实例标识。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RunningMultiInstanceInfo-instanceKey: string--><!--Device-RunningMultiInstanceInfo-instanceKey: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## pids

```TypeScript
pids: Array<int>
```

应用的进程ID集合。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RunningMultiInstanceInfo-pids: Array<int>--><!--Device-RunningMultiInstanceInfo-pids: Array<int>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: int
```

表示应用程序的UID。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RunningMultiInstanceInfo-uid: int--><!--Device-RunningMultiInstanceInfo-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

