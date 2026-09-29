# SimState

```TypeScript
export enum SimState
```

SIM卡状态。

**起始版本：** 6

<!--Device-sim-export enum SimState--><!--Device-sim-export enum SimState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_UNKNOWN

```TypeScript
SIM_STATE_UNKNOWN = 0
```

SIM卡状态未知，即无法获取准确的状态。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_UNKNOWN = 0--><!--Device-SimState-SIM_STATE_UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_NOT_PRESENT

```TypeScript
SIM_STATE_NOT_PRESENT = 1
```

表示SIM卡处于not present状态，即卡槽中没有插入SIM卡。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_NOT_PRESENT = 1--><!--Device-SimState-SIM_STATE_NOT_PRESENT = 1-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_LOCKED

```TypeScript
SIM_STATE_LOCKED = 2
```

表示SIM卡处于locked状态，即SIM卡被PIN、PUK或网络锁锁定。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_LOCKED = 2--><!--Device-SimState-SIM_STATE_LOCKED = 2-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_NOT_READY

```TypeScript
SIM_STATE_NOT_READY = 3
```

表示SIM卡处于not ready状态，即SIM卡在位但无法正常工作。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_NOT_READY = 3--><!--Device-SimState-SIM_STATE_NOT_READY = 3-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_READY

```TypeScript
SIM_STATE_READY = 4
```

表示SIM卡处于ready状态，即SIM卡在位且工作正常。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_READY = 4--><!--Device-SimState-SIM_STATE_READY = 4-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## SIM_STATE_LOADED

```TypeScript
SIM_STATE_LOADED = 5
```

表示SIM卡处于loaded状态，即SIM卡在位且所有卡文件加载完毕。

**起始版本：** 6

<!--Device-SimState-SIM_STATE_LOADED = 5--><!--Device-SimState-SIM_STATE_LOADED = 5-End-->

**系统能力：** SystemCapability.Telephony.CoreService
