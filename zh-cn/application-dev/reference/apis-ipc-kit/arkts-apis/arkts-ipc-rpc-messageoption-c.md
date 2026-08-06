# MessageOption

公共消息选项，使用指定的标志类型，构造指定的MessageOption对象。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-rpc-class MessageOption--><!--Device-rpc-class MessageOption-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## TF_ACCEPT_FDS

```TypeScript
static get TF_ACCEPT_FDS(): int
```

Indicates the sendRequest API for returning the file descriptor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-static get TF_ACCEPT_FDS(): int--><!--Device-MessageOption-static get TF_ACCEPT_FDS(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the sendRequest API for returning the file descriptor. |

## TF_ASYNC

```TypeScript
static get TF_ASYNC(): int
```

Indicates asynchronous call.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-static get TF_ASYNC(): int--><!--Device-MessageOption-static get TF_ASYNC(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating asynchronous call. |

## TF_SYNC

```TypeScript
static get TF_SYNC(): int
```

Indicates synchronous call.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-static get TF_SYNC(): int--><!--Device-MessageOption-static get TF_SYNC(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating synchronous call. |

## TF_WAIT_TIME

```TypeScript
static get TF_WAIT_TIME(): int
```

Indicates the wait time for RPC, in seconds. It is NOT used in IPC case.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-static get TF_WAIT_TIME(): int--><!--Device-MessageOption-static get TF_WAIT_TIME(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Return vaule indicating the wait time for RPC, in seconds. It is NOT used in IPC case. |

## constructor

```TypeScript
constructor(syncFlags?: number, waitTime?: number)
```

MessageOption构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-constructor(syncFlags?: number, waitTime?: number)--><!--Device-MessageOption-constructor(syncFlags?: number, waitTime?: number)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| syncFlags | number | 否 | 同步调用或异步调用标志。取值范围：{0, 1}。同步调用标志：0（当需要立即获取响应结果时选择）；异步调用标志：1（当不需要立即获取响应结果时选择）。不传入时默认为0（同步调用）。 |
| waitTime | number | 否 | 调用rpc最长等待时间（单位：秒）。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：(0, 3000]。当RPC调用耗时较长时，可适当增加等待时间；当需要快速响应时，可适当减少等待时间。不传入时使用默认等待时间8秒。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(syncFlags?: number, waitTime?: number) {
    super(syncFlags, waitTime);
  }
}
```

## constructor

```TypeScript
constructor(async?: boolean)
```

MessageOption构造函数。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-constructor(async?: boolean)--><!--Device-MessageOption-constructor(async?: boolean)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| async | boolean | 否 | 是否异步调用。true表示异步调用（当不需要立即获取响应结果时选择），false表示同步调用（当需要立即获取响应结果时选择）。不传入时默认为false（同步调用）。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(async: boolean) {
    super(async);
  }
}
```

## constructor

```TypeScript
constructor(isAsync: boolean)
```

A constructor used to create a MessageOption instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-constructor(isAsync: boolean)--><!--Device-MessageOption-constructor(isAsync: boolean)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAsync | boolean | 是 | Specifies whether the SendRequest is called synchronously (default) or asynchronously. |

**示例：**

```TypeScript
// ArkTS-Sta示例
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.MessageOption {
  constructor(isAsync: boolean) {
    super(isAsync);
  }
}
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a MessageOption instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-constructor()--><!--Device-MessageOption-constructor()-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**示例：**

```TypeScript
// ArkTS-Sta示例
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor() {
    super();
  }
}
```

## constructor

```TypeScript
constructor(syncFlags: int)
```

A constructor used to create a MessageOption instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-constructor(syncFlags: int)--><!--Device-MessageOption-constructor(syncFlags: int)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| syncFlags | int | 是 | Specifies whether the SendRequest is called synchronously (default) or asynchronously. |

**示例：**

```TypeScript
// ArkTS-Sta示例
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.MessageOption {
  constructor(syncFlags: int) {
    super(syncFlags);
  }
}
```

## constructor

```TypeScript
constructor(syncFlags: int, waitTime: int)
```

A constructor used to create a MessageOption instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-MessageOption-constructor(syncFlags: int, waitTime: int)--><!--Device-MessageOption-constructor(syncFlags: int, waitTime: int)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| syncFlags | int | 是 | Specifies whether the SendRequest is called synchronously (default) or asynchronously. |
| waitTime | int | 是 | Maximum wait time for a RPC call, in seconds. The default value is **TF\_\_\_ESCAPED\_UNDERSCORE\_\_\_WAIT\_\_\_ESCAPED\_UNDERSCORE\_\_\_TIME**. |

**示例：**

```TypeScript
// ArkTS-Sta示例
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.MessageOption {
  constructor(syncFlags: int, waitTime: int) {
    super(syncFlags, waitTime);
  }
}
```

## getFlags

ArkTS-Dyn:
```TypeScript
getFlags(): number
```

ArkTS-Sta:
```TypeScript
getFlags(): int
```

获取同步调用或异步调用标志。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-getFlags(): int--><!--Device-MessageOption-getFlags(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 调用成功返回同步调用或异步调用标志。同步调用标志：0，异步调用标志：1。 |

**示例：**

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

ArkTS-Dyn:
```TypeScript
getWaitTime(): number
```

ArkTS-Sta:
```TypeScript
getWaitTime(): int
```

获取rpc调用的最长等待时间。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-getWaitTime(): int--><!--Device-MessageOption-getWaitTime(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | rpc最长等待时间（单位：秒）。 |

**示例：**

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

获取 [sendMessageRequest]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 调用中确定同步或是异步的标志。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-isAsync(): boolean--><!--Device-MessageOption-isAsync(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：异步调用成功，false：同步调用成功。 |

**示例：**

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

设置 [sendMessageRequest]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 调用中确定同步或是异步的标志。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-setAsync(isAsync: boolean): void--><!--Device-MessageOption-setAsync(isAsync: boolean): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isAsync | boolean | 是 | true：表示异步调用标志，false：表示同步调用标志。 |

**示例：**

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

ArkTS-Dyn:
```TypeScript
setFlags(flags: number): void
```

ArkTS-Sta:
```TypeScript
setFlags(flags: int): void
```

设置同步调用或异步调用标志。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-setFlags(flags: int): void--><!--Device-MessageOption-setFlags(flags: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flags | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 同步调用或异步调用标志。取值范围：{0, 1}。同步调用标志：0；异步调用标志：1。 |

**示例：**

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

ArkTS-Dyn:
```TypeScript
setWaitTime(waitTime: number): void
```

ArkTS-Sta:
```TypeScript
setWaitTime(waitTime: int): void
```

设置rpc调用最长等待时间。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-setWaitTime(waitTime: int): void--><!--Device-MessageOption-setWaitTime(waitTime: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| waitTime | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | rpc调用最长等待时间（单位：秒），取值范围：(0，3000] |

**示例：**

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

指示 [sendMessageRequest]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 接口可以传递文件描述符。

**类型：** number

**默认值：** 16

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-static readonly TF_ACCEPT_FDS: number--><!--Device-MessageOption-static readonly TF_ACCEPT_FDS: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## TF_ASYNC

```TypeScript
static readonly TF_ASYNC: number
```

异步调用标识。

**类型：** number

**默认值：** 1

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-static readonly TF_ASYNC: number--><!--Device-MessageOption-static readonly TF_ASYNC: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## TF_SYNC

```TypeScript
static readonly TF_SYNC: number
```

同步调用标识。

**类型：** number

**默认值：** 0

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-static readonly TF_SYNC: number--><!--Device-MessageOption-static readonly TF_SYNC: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## TF_WAIT_TIME

```TypeScript
static readonly TF_WAIT_TIME: number
```

RPC等待时间（单位：秒），IPC场景下无效。默认等待为8秒（不建议修改等待时间）。

**类型：** number

**默认值：** 4 [since 7 - 10]
@default 8 [since 11]

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MessageOption-static readonly TF_WAIT_TIME: number--><!--Device-MessageOption-static readonly TF_WAIT_TIME: number-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

