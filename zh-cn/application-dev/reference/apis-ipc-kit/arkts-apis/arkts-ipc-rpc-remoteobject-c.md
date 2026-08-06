# RemoteObject

实现远程对象。服务提供者必须继承此类。

**继承/实现关系：** RemoteObject extends [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-rpc-class RemoteObject extends IRemoteObject--><!--Device-rpc-class RemoteObject extends IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## attachLocalInterface

```TypeScript
attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void
```

此接口用于把接口描述符和IRemoteBroker对象绑定。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [modifyLocalInterface](arkts-ipc-rpc-remoteobject-c.md#modifylocalinterface)(localInterface:

<!--Device-RemoteObject-attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void--><!--Device-RemoteObject-attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localInterface | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 将与描述符绑定的IRemoteBroker对象。 |
| descriptor | string | 是 | 用于与IRemoteBroker对象绑定的描述符。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
    this.attachLocalInterface(this, descriptor);
  }
  addDeathRecipient(recipient: MyDeathRecipient, flags: number): boolean {
    // 方法逻辑需开发者根据业务需要实现
    return true;
  }
  removeDeathRecipient(recipient: MyDeathRecipient, flags: number): boolean {
    // 方法逻辑需开发者根据业务需要实现
    return true;
  }
}
let testRemoteObject = new TestRemoteObject("testObject");
```

## constructor

```TypeScript
constructor(descriptor: string)
```

RemoteObject构造函数。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-constructor(descriptor: string)--><!--Device-RemoteObject-constructor(descriptor: string)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符，其长度应小于40960。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
}
```

## getCallingPid

ArkTS-Dyn:
```TypeScript
getCallingPid(): number
```

ArkTS-Sta:
```TypeScript
getCallingPid(): int
```

获取通信对端的进程Pid。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-getCallingPid(): int--><!--Device-RemoteObject-getCallingPid(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回通信对端的进程Pid。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingPid: ' + testRemoteObject.getCallingPid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingUid: ' + testRemoteObject.getCallingUid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## getCallingUid

ArkTS-Dyn:
```TypeScript
getCallingUid(): number
```

ArkTS-Sta:
```TypeScript
getCallingUid(): int
```

获取通信对端的进程Uid。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-getCallingUid(): int--><!--Device-RemoteObject-getCallingUid(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | Return the UID of the { |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingUid: ' + testRemoteObject.getCallingUid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingPid: ' + testRemoteObject.getCallingPid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## getDescriptor

```TypeScript
getDescriptor(): string
```

获取对象的接口描述符。接口描述符为字符串。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-getDescriptor(): string--><!--Device-RemoteObject-getDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testObject = new TestRemoteObject("ipcTest");
  let descriptor = testObject.getDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is ' + descriptor);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

查询接口描述符。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#getDescriptor](arkts-ipc-rpc-iremoteobject-c.md#getdescriptor)()

<!--Device-RemoteObject-getInterfaceDescriptor(): string--><!--Device-RemoteObject-getInterfaceDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let descriptor = testRemoteObject.getInterfaceDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is: ' + descriptor);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## getLocalInterface

```TypeScript
getLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-getLocalInterface(descriptor: string): IRemoteBroker--><!--Device-RemoteObject-getLocalInterface(descriptor: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符的字符串，其长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回绑定到指定接口描述符的IRemoteBroker对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The string length is greater than or equal to 40960;4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let testRemoteObject = new TestRemoteObject("testObject");
  testRemoteObject.getLocalInterface("testObject");
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## modifyLocalInterface

```TypeScript
modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void
```

此接口用于把接口描述符和IRemoteBroker对象绑定。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void--><!--Device-RemoteObject-modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localInterface | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 将与描述符绑定的IRemoteBroker对象。 |
| descriptor | string | 是 | 用于与IRemoteBroker对象绑定的描述符，其长度应小于40960。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The string length is greater than or equal to 40960;4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MyDeathRecipient implements rpc.DeathRecipient {
  onRemoteDied() {
    hilog.info(0x0000, 'testTag', 'server died');
  }
}
class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
    try {
      this.modifyLocalInterface(this, descriptor);
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
      hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
    }
  }
  registerDeathRecipient(recipient: MyDeathRecipient, flags: number) {
    // 方法逻辑需开发者根据业务需要实现
  }
  unregisterDeathRecipient(recipient: MyDeathRecipient, flags: number) {
    // 方法逻辑需开发者根据业务需要实现
  }
}
let testRemoteObject = new TestRemoteObject("testObject");
```

## onRemoteMessageRequest

ArkTS-Dyn:
```TypeScript
onRemoteMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): boolean | Promise<boolean>
```

ArkTS-Sta:
```TypeScript
onRemoteMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): boolean | Promise<boolean>
```

sendMessageRequest请求的响应处理函数，服务端在该函数里同步或异步地处理请求，回复结果。 > **说明：** > >开发者应优先选择重写onRemoteMessageRequest方法，其中可以自由实现同步和异步的消息处理。 > >开发者同时重写onRemoteRequest和onRemoteMessageRequest方法时，仅onRemoteMessageRequest方法生效。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): boolean | Promise<boolean>--><!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): boolean | Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 对端发送的服务请求码。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 携带客户端调用参数的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 写入结果的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示操作是同步还是异步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 若在onRemoteMessageRequest中同步处理请求，则返回一个布尔值。返回true表示操作成功，返回false表示操作失败。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// 重写onRemoteMessageRequest方法同步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
// 重写onRemoteMessageRequest方法同步处理请求
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

ArkTS-Dyn示例：

```TypeScript
// 重写onRemoteMessageRequest方法异步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

ArkTS-Sta示例：

```TypeScript
// 重写onRemoteMessageRequest方法异步处理请求
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return new Promise<boolean>((resolve) => {
        resolve(false);
      });
    }
    return new Promise<boolean>((resolve) => {
      resolve(true);
    });
  }
}
```

ArkTS-Dyn示例：

```TypeScript
// 同时重写onRemoteMessageRequest和onRemoteRequest方法同步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
  // 同时调用仅会执行onRemoteMessageRequest
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
}
```

## onRemoteMessageRequest

ArkTS-Dyn:
```TypeScript
onRemoteMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callingInfo?: CallingInfo
    ): boolean | Promise<boolean>
```

ArkTS-Sta:
```TypeScript
onRemoteMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callingInfo?: CallingInfo
    ): boolean | Promise<boolean>
```

sendMessageRequest请求的响应处理函数，服务端在该函数里同步或异步地处理请求，回复结果，该接口可从入参callingInfo中获取IPC上下文信息。 > **说明：** > > 开发者应优先选择重写带有CallingInfo参数的onRemoteMessageRequest方法，其中可以自由实现同步和异步的消息处理。 > > 开发者同时重写onRemoteRequest和onRemoteMessageRequest方法时，仅onRemoteMessageRequest方法生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callingInfo?: CallingInfo    ): boolean | Promise<boolean>--><!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callingInfo?: CallingInfo    ): boolean | Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 对端发送的服务请求码。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 携带客户端调用参数的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 写入结果的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示操作是同步还是异步。 |
| callingInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 获取IPC上下文信息。不传此参数时，默认为undefined。当需要获取调用者的PID、UID、TokenId或设备ID等信息时传入此参数，可通过callingInfo.callerPid等方式获取。不传入时无法直接获取IPC上下文信息，需通过rpc.IPCSkeleton其他方法（如getCallingPid、getCallingUid等）获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - 若在onRemoteMessageRequest中同步处理请求，则返回一个布尔值。返回true表示操作成功，返回false表示操作失败。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// 重写onRemoteMessageRequest方法同步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: rpc.CallingInfo): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      let pid = callingInfo?.callerPid;
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
// 重写onRemoteMessageRequest方法同步处理请求
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo: rpc.CallingInfo): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

ArkTS-Dyn示例：

```TypeScript
// 重写onRemoteMessageRequest方法异步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  async onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: rpc.CallingInfo): Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
      let pid = callingInfo?.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    await new Promise((resolve: (data: rpc.RequestResult) => void) => {
      setTimeout(resolve, 100);
    })
    return true;
  }
}
```

ArkTS-Dyn示例：

```TypeScript
// 同时重写onRemoteMessageRequest和onRemoteRequest方法同步处理请求
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
     if (code === 1) {
        hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
        return true;
     } else {
        hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
        return false;
     }
  }
  // 同时调用仅会执行onRemoteMessageRequest
  // 动态语言中不支持重写onRemoteMessageRequest，此处只提供带有CallingInfo的示例
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo?: rpc.CallingInfo): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      let pid = callingInfo?.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
}
```

ArkTS-Sta示例：

```TypeScript
// 同时重写带有CallingInfo和不带CallingInfo的onRemoteMessageRequest方法及onRemoteRequest方法同步处理请求
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean {
     if (code === 1) {
        hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
        return true;
     } else {
        hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
        return false;
     }
  }

  // 同时调用仅会执行该onRemoteMessageRequest
  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption, callingInfo: rpc.CallingInfo): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: sync onRemoteMessageRequest is called');
      let pid = callingInfo.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
  // ArkTS-Sta无onRemoteRequest方法
}
```

## onRemoteRequest

```TypeScript
onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

sendRequest请求的响应处理函数，服务端在该函数里处理请求，回复结果。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [onRemoteMessageRequest](arkts-ipc-rpc-remoteobject-c.md#onremotemessagerequest)(code:

<!--Device-RemoteObject-onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-RemoteObject-onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 对端发送的服务请求码。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 携带客户端调用参数的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 写入结果的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示操作是同步还是异步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：操作成功，false：操作失败。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: onRemoteRequest called');
      return true;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
  }
}
```

## queryLocalInterface

```TypeScript
queryLocalInterface(descriptor: string): IRemoteBroker
```

查询并获取当前接口描述符对应的远端对象是否已经存在。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#getLocalInterface](arkts-ipc-rpc-iremoteobject-c.md#getlocalinterface)(descriptor:

<!--Device-RemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker--><!--Device-RemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 需要查询的接口描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 如果接口描述符对应的远端对象存在，则返回该远端对象，否则返回Null。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }

  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}

try {
  let testRemoteObject = new TestRemoteObject("testObject");
  testRemoteObject.queryLocalInterface("testObject");
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## sendMessageRequest

ArkTS-Dyn:
```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

ArkTS-Sta:
```TypeScript
sendMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

以同步或异步方式向对端进程发送MessageSequence消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结 果将在sendMessageRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>--><!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RequestResult&gt; | Promise对象，返回发送请求的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.Failed to obtain the passed object instance. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString("hello");
  testRemoteObject.sendMessageRequest(1, data, reply, option)
    .then((result: rpc.RequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + JSON.stringify(e));
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + error);
}
```

ArkTS-Sta示例：

```TypeScript
import rpc from '@ohos.rpc';
import hilog from 'ohos.hilog';
import { BusinessError } from '@ohos.base';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(code: int, data: rpc.MessageSequence, reply: rpc.MessageSequence,
    option: rpc.MessageOption): boolean | Promise<boolean> {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString("hello");
  testRemoteObject.sendMessageRequest(1, data, reply, option)
    .then((result: rpc.RequestResult) => {
      if (result.errCode === 0) {
        hilog.info(0x0000, 'testTag', 'sendMessageRequest got result');
        let num = result.reply.readInt();
        let msg = result.reply.readString();
        hilog.info(0x0000, 'testTag', 'reply num: ' + num);
        hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
      } else {
        hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, errCode: ' + result.errCode);
      }
    }).catch((e: Error) => {
      hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + JSON.stringify(e));
    }).finally (() => {
      hilog.info(0x0000, 'testTag', 'sendMessageRequest ends, reclaim parcel');
      data.reclaim();
      reply.reclaim();
    });
} catch (error) {
  hilog.error(0x0000, 'testTag', 'sendMessageRequest failed, error: ' + error);
}
```

## sendMessageRequest

ArkTS-Dyn:
```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callback: AsyncCallback<RequestResult>
    ): void
```

ArkTS-Sta:
```TypeScript
sendMessageRequest(
      code: int,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callback: AsyncCallback<RequestResult>
    ): void
```

以同步或异步方式向对端进程发送MessageSequence消息。使用callback异步回调。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则 将在sendMessageRequest返回时收到回调，回复内容在reply报文里。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void--><!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageSequence对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageSequence对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RequestResult&gt; | 是 | 回调函数。当消息发送成功时，可从RequestResult中读取服务端返回的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.Failed to obtain the passed object instance. |

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收到回 复，回复内容在reply报文里。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-RemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：发送成功，false：发送失败。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class testRemoteObject extends rpc.RemoteObject {
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  let ret: boolean = testRemoteObject.sendRequest(1, data, reply, option);
  if (ret) {
    hilog.info(0x0000, 'testTag', 'sendRequest got result');
    let msg = reply.readString();
    hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
  } else {
    hilog.error(0x0000, 'testTag', 'sendRequest failed');
  }
  hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
  data.reclaim();
  reply.reclaim();
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## sendRequest

```TypeScript
sendRequest(
      code: number,
      data: MessageParcel,
      reply: MessageParcel,
      options: MessageOption
    ): Promise<SendRequestResult>
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结果将 在sendRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>--><!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SendRequestResult&gt; | Promise对象，返回发送请求的响应结果。 |

**示例：**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel, option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject("testObject");
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString("hello");
  let a = testRemoteObject.sendRequest(1, data, reply, option) as Object;
  let b = a as Promise<rpc.SendRequestResult>;
  b.then((result: rpc.SendRequestResult) => {
    if (result.errCode === 0) {
      hilog.info(0x0000, 'testTag', 'sendRequest got result');
      let num = result.reply.readInt();
      let msg = result.reply.readString();
      hilog.info(0x0000, 'testTag', 'reply num: ' + num);
      hilog.info(0x0000, 'testTag', 'reply msg: ' + msg);
    } else {
      hilog.error(0x0000, 'testTag', 'sendRequest failed, errCode: ' + result.errCode);
    }
  }).catch((e: Error) => {
    hilog.error(0x0000, 'testTag', 'sendRequest failed, error: ' + JSON.stringify(e));
  }).finally (() => {
    hilog.info(0x0000, 'testTag', 'sendRequest ends, reclaim parcel');
    data.reclaim();
    reply.reclaim();
  });
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## sendRequest

```TypeScript
sendRequest(
      code: number,
      data: MessageParcel,
      reply: MessageParcel,
      options: MessageOption,
      callback: AsyncCallback<SendRequestResult>
    ): void
```

以同步或异步方式向对端进程发送MessageParcel消息。使用callback异步回调。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在 sendRequest返回时收到回调，回复内容在reply报文里。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [rpc.IRemoteObject#sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void--><!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SendRequestResult&gt; | 是 | 接收发送结果的回调。 |

