# MessageOption

```TypeScript
class MessageOption
```

Defines the options used to construct the **MessageOption** object.

**Since:** 7

<!--Device-rpc-class MessageOption--><!--Device-rpc-class MessageOption-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## constructor

```TypeScript
constructor(syncFlags?: number, waitTime?: number)
```

A constructor used to create a **MessageOption** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-constructor(syncFlags?: number, waitTime?: number)--><!--Device-MessageOption-constructor(syncFlags?: number, waitTime?: number)-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| syncFlags | number | No | Synchronous or asynchronous call flag. The value range is {0, 1}. The value **0** indicates synchronous call (use this value when you need to obtain the response immediately), and the value **1** indicates asynchronous call (use this value when you do not need to obtain the response immediately). If this parameter is not specified, **0** (synchronous call) is used by default. |
| waitTime | number | No | Maximum wait time for an RPC call, in seconds.<br>Default value: **8** <br>Value range: (0, 3000]. If an RPC call takes a long time, you can increase the wait time. If a quick response is required, you can reduce the wait time. If this parameter is not specified, the default wait time of 8 seconds is used. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(syncFlags?: number,waitTime?: number) {
    super(syncFlags,waitTime);
  }
}
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(async?: boolean)
```

A constructor used to create a **MessageOption** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-constructor(async?: boolean)--><!--Device-MessageOption-constructor(async?: boolean)-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| async | boolean | No | Whether the call is asynchronous. **true** indicates an asynchronous call (use this value when you do not need to obtain the response immediately), and **false** indicates a synchronous call (use this value when you need to obtain the response immediately). If this parameter is not specified, the default value is **false** (synchronous call). |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(async: boolean) {
    super(async);
  }
}
```

## getFlags

```TypeScript
getFlags(): number
```

Obtains the call flag, which can be synchronous or asynchronous.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-getFlags(): int--><!--Device-MessageOption-getFlags(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Call flag obtained. **0**: synchronous call flag; **1**: asynchronous call flag. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  hilog.info(0x0000, 'testTag', 'Succeeded in creating object');
  let flag = option.getFlags();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getFlags, flag is ' + flag);
  option.setFlags(rpc.MessageOption.TF_ASYNC);
  hilog.info(0x0000, 'testTag', 'Succeeded in running setFlags');
  let flag2 = option.getFlags();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getFlags, flag2 is ' + flag2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getWaitTime

```TypeScript
getWaitTime(): number
```

Obtains the maximum wait time for an RPC call.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-getWaitTime(): int--><!--Device-MessageOption-getWaitTime(): int-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum wait time for an RPC call, in seconds. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let time = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getWaitTime, time is ' + time);
  option.setWaitTime(16);
  let time2 = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getWaitTime, time is ' + time2);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## isAsync

```TypeScript
isAsync(): boolean
```

Checks whether [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest) is called asynchronously.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-isAsync(): boolean--><!--Device-MessageOption-isAsync(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if **SendMessageRequest** is called asynchronously; returns **false** if it is called synchronously. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  let result = option.isAsync();
} catch (error) {
  hilog.info(0x0000, 'testTag', 'error ' + error);
}
```

## setAsync

```TypeScript
setAsync(isAsync: boolean): void
```

Sets whether to call [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest) asynchronously.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-setAsync(isAsync: boolean): void--><!--Device-MessageOption-setAsync(isAsync: boolean): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAsync | boolean | Yes | Whether to execute the call asynchronously. The value **true** means to execute the call asynchronously; the value **false** means to execute the call synchronously. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setAsync(true);
} catch (error) {
  hilog.info(0x0000, 'testTag', 'error ' + error);
}
```

## setFlags

```TypeScript
setFlags(flags: number): void
```

Sets the call flag, which can be synchronous or asynchronous.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-setFlags(flags: int): void--><!--Device-MessageOption-setFlags(flags: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flags | number | Yes | Call flag to set. The value range is {0, 1}. **0**: synchronous call flag; **1**: asynchronous call flag. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setFlags(rpc.MessageOption.TF_ASYNC);
  hilog.info(0x0000, 'testTag', 'Succeeded in running setFlags');
  let flag = option.getFlags();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getFlags, flag is ' + flag);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## setWaitTime

```TypeScript
setWaitTime(waitTime: number): void
```

Sets the maximum wait time for an RPC call.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-MessageOption-setWaitTime(waitTime: int): void--><!--Device-MessageOption-setWaitTime(waitTime: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| waitTime | number | Yes | Maximum wait time for an RPC call, in seconds. The value range is (0, 3000]. |

**Examples**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let option = new rpc.MessageOption();
  option.setWaitTime(16);
  let time = option.getWaitTime();
  hilog.info(0x0000, 'testTag', 'Succeeded in running getWaitTime, time is ' + time);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## TF_ACCEPT_FDS

```TypeScript
static readonly TF_ACCEPT_FDS: number
```

Whether the [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest) API can transfer the file descriptor.

**Type:** number

**Default:** 16

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-static readonly TF_ACCEPT_FDS: number--><!--Device-MessageOption-static readonly TF_ACCEPT_FDS: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## TF_ASYNC

```TypeScript
static readonly TF_ASYNC: number
```

Asynchronous call.

**Type:** number

**Default:** 1

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-static readonly TF_ASYNC: number--><!--Device-MessageOption-static readonly TF_ASYNC: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## TF_SYNC

```TypeScript
static readonly TF_SYNC: number
```

Synchronous call.

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-static readonly TF_SYNC: number--><!--Device-MessageOption-static readonly TF_SYNC: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## TF_WAIT_TIME

```TypeScript
static readonly TF_WAIT_TIME: number
```

RPC wait time, in seconds. This parameter cannot be used in IPC. The default waiting time is 8 seconds. You are advised not to change the waiting time.

**Type:** number

**Default:** 
- API versions 7 to 10: 4
- API version 11+: 8

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-MessageOption-static readonly TF_WAIT_TIME: number--><!--Device-MessageOption-static readonly TF_WAIT_TIME: number-End-->

**System capability:** SystemCapability.Communication.IPC.Core
