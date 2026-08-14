# CallingInfo

IPC上下文信息，包括PID和UID、本端和对端设备ID、检查接口调用是否在同一设备上。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-rpc-class CallingInfo--><!--Device-rpc-class CallingInfo-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## callerPid

```TypeScript
readonly callerPid: number
```

调用者的PID，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly callerPid: number--><!--Device-CallingInfo-readonly callerPid: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## callerTokenId

```TypeScript
readonly callerTokenId: number
```

调用者的TokenId，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly callerTokenId: number--><!--Device-CallingInfo-readonly callerTokenId: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## callerUid

```TypeScript
readonly callerUid: number
```

调用者的UID，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly callerUid: number--><!--Device-CallingInfo-readonly callerUid: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## isLocalCalling

```TypeScript
readonly isLocalCalling: boolean
```

当前通信对端是否为本设备进程。true：调用在同一台设备（IPC场景），false：调用未在同一台设备（RPC场景）。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly isLocalCalling: boolean--><!--Device-CallingInfo-readonly isLocalCalling: boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## localDeviceId

```TypeScript
readonly localDeviceId: string
```

本端设备的设备ID，仅RPC场景有效。

**类型：** string

**默认值：** @syscap SystemCapability.Communication.IPC.Core @FaAndStageModel

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly localDeviceId: string--><!--Device-CallingInfo-readonly localDeviceId: string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## remoteDeviceId

```TypeScript
readonly remoteDeviceId: string
```

对端设备的设备ID，仅RPC场景有效。

**类型：** string

**默认值：** @syscap SystemCapability.Communication.IPC.Core @FaAndStageModel

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CallingInfo-readonly remoteDeviceId: string--><!--Device-CallingInfo-readonly remoteDeviceId: string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

