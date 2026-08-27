# CallingInfo

IPC上下文信息，包括PID和UID、本端和对端设备ID、检查接口调用是否在同一设备上。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## callerPid

```TypeScript
readonly callerPid: number
```

调用者的PID，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

## callerTokenId

```TypeScript
readonly callerTokenId: number
```

调用者的TokenId，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

## callerUid

```TypeScript
readonly callerUid: number
```

调用者的UID，仅IPC场景有效。

**类型：** number

**默认值：** -1

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

## isLocalCalling

```TypeScript
readonly isLocalCalling: boolean
```

当前通信对端是否为本设备进程。true：调用在同一台设备（IPC场景），false：调用未在同一台设备（RPC场景）。

**类型：** boolean

**默认值：** true

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class Stub extends rpc.RemoteObject {
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    try {
      let isLocalCalling = rpc.IPCSkeleton.isLocalCalling();
      hilog.info(0x0000, 'testTag', 'RpcServer: isLocalCalling is ' + isLocalCalling);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'error ' + error);
    }
    return true;
  }
}
```

## localDeviceId

```TypeScript
readonly localDeviceId: string
```

本端设备的设备ID，仅RPC场景有效。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core

## remoteDeviceId

```TypeScript
readonly remoteDeviceId: string
```

对端设备的设备ID，仅RPC场景有效。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Communication.IPC.Core
