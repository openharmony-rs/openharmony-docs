# RemoteObject

```TypeScript
class RemoteObject extends IRemoteObject
```

实现远程对象。服务提供者必须继承此类。

**继承/实现关系：** RemoteObject extends [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)

**起始版本：** 7

<!--Device-rpc-class RemoteObject extends IRemoteObject--><!--Device-rpc-class RemoteObject extends IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## constructor

```TypeScript
constructor(descriptor: string)
```

RemoteObject构造函数。

**起始版本：** 7

<!--Device-RemoteObject-constructor(descriptor: string)--><!--Device-RemoteObject-constructor(descriptor: string)-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符，其长度应小于40960。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';

class TestRemoteObject extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
}
```

## getCallingPid

```TypeScript
getCallingPid(): number
```

获取通信对端的进程Pid。

**起始版本：** 7

<!--Device-RemoteObject-getCallingPid(): int--><!--Device-RemoteObject-getCallingPid(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回通信对端的进程Pid。 |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingPid: ' + testRemoteObject.getCallingPid());
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## getCallingUid

```TypeScript
getCallingUid(): number
```

获取通信对端的进程Uid。

**起始版本：** 7

<!--Device-RemoteObject-getCallingUid(): int--><!--Device-RemoteObject-getCallingUid(): int-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回通信对端的进程Uid。 |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  hilog.info(0x0000, 'testTag', 'RpcServer: getCallingUid: ' + testRemoteObject.getCallingUid());
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

**示例**

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
  let testObject = new TestRemoteObject('ipcTest');
  let descriptor = testObject.getDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is ' + descriptor);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  hilog.error(0x0000, 'testTag', 'errorCode ' + e.code);
  hilog.error(0x0000, 'testTag', 'errorMessage ' + e.message);
}
```

## getLocalInterface

```TypeScript
getLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 9

<!--Device-RemoteObject-getLocalInterface(descriptor: string): IRemoteBroker--><!--Device-RemoteObject-getLocalInterface(descriptor: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符的字符串，其长度应小于40960。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 返回绑定到指定接口描述符的IRemoteBroker对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  testRemoteObject.getLocalInterface('testObject');
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

<!--Device-RemoteObject-modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void--><!--Device-RemoteObject-modifyLocalInterface(localInterface: IRemoteBroker, descriptor: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localInterface | [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 是 | 将与描述符绑定的IRemoteBroker对象。 |
| descriptor | string | 是 | 用于与IRemoteBroker对象绑定的描述符，其长度应小于40960。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

**示例**

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
let testRemoteObject = new TestRemoteObject('testObject');
```

## onRemoteMessageRequest

```TypeScript
onRemoteMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): boolean | Promise<boolean>
```

Sets an entry for receiving requests. <p>This method is implemented by the remote service provider. You need to override this method with your own service logic when you are using IPC.

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): boolean | Promise<boolean>--><!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): boolean | Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Service request code sent by the remote end. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object that holds the parameters called by the client. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object to which the result is written. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Whether the operation is synchronous or asynchronous. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean &#124; Promise&lt;boolean&gt; | If the request is processed synchronously in **onRemoteMessageRequest**, a Boolean value is returned. The value **true** means that the operation is successful, and **false** means the opposite.<br>- If the request is processed asynchronously in **onRemoteMessageRequest**, a promise object is returned. The value **true** means that the operation is successful, and **false** means the opposite. |

**示例**

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

<a id="onremotemessagerequest-1"></a>

## onRemoteMessageRequest

```TypeScript
onRemoteMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callingInfo?: CallingInfo
    ): boolean | Promise<boolean>
```

Sets an entry for receiving requests. <p>This method is implemented by the remote service provider. You need to override this method with your own service logic when you are using IPC.

**起始版本：** 23

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callingInfo?: CallingInfo    ): boolean | Promise<boolean>--><!--Device-RemoteObject-onRemoteMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callingInfo?: CallingInfo    ): boolean | Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Service request code sent by the remote end. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object that holds the parameters called by the client. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object to which the result is written. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Whether the operation is synchronous or asynchronous. |
| callingInfo | [CallingInfo](arkts-ipc-rpc-callinginfo-c.md) | 否 | IPC context. If this parameter is not specified, it defaults to **undefined**. Pass this parameter when you need to obtain information such as the caller's PID, UID, token ID, or device ID. You can obtain this information via **callingInfo.callerPid** and similar properties. If this parameter is not passed, IPC context information cannot be obtained directly, and you need to use other methods of **rpc.IPCSkeleton**, such as **getCallingPid** and **getCallingUid** |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean &#124; Promise&lt;boolean&gt; | 同步模式成功时返回true，失败返回false；异步模式返回promise对象 |

**示例**

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
    option: rpc.MessageOption, callingInfo?: rpc.CallingInfo): boolean | Promise<boolean> {
    if (code === 1) {
      hilog.info(0x0000, 'testTag', 'RpcServer: async onRemoteMessageRequest is called');
      let pid = callingInfo?.callerPid;
    } else {
      hilog.error(0x0000, 'testTag', 'RpcServer: unknown code: ' + code);
      return false;
    }
    return true;
  }
}
```

## sendMessageRequest

```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

Sends a [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) message to the peer process in synchronous or asynchronous mode. <p>If options indicates the asynchronous mode, a promise will be fulfilled immediately and the reply message does not contain any content. If options indicates the synchronous mode, a promise will be fulfilled when the response to sendMessageRequest is returned, and the reply message contains the returned information.

**起始版本：** 9

<!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>--><!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object holding the data to send. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Request sending mode, which can be synchronous (default) or asynchronous. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | Promise used to return the response to the request. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString('hello');
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

<a id="sendmessagerequest-1"></a>

## sendMessageRequest

```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption,
      callback: AsyncCallback<RequestResult>
    ): void
```

Sends a [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) message to the peer process in synchronous or asynchronous mode. <p>If options indicates the asynchronous mode, a callback will be invoked immediately and the reply message does not contain any content. If options indicates the synchronous mode, a callback will be invoked when the response to sendMessageRequest is returned, and the reply message contains the returned information.

**起始版本：** 9

<!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void--><!--Device-RemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object holding the data to send. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | **MessageSequence** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Request sending mode, which can be synchronous (default) or asynchronous. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | 是 | Callback used to return the result. When the message is sent successfully, the data returned by the server can be read from **RequestResult**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageSequence.create();
  let reply = rpc.MessageSequence.create();
  data.writeInt(1);
  data.writeString('hello');
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

## attachLocalInterface

```TypeScript
attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void
```

此接口用于把接口描述符和IRemoteBroker对象绑定。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [modifyLocalInterface](#modifylocalinterface)(localInterface: IRemoteBroker, descriptor: string)

<!--Device-RemoteObject-attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void--><!--Device-RemoteObject-attachLocalInterface(localInterface: IRemoteBroker, descriptor: string): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localInterface | [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 是 | 将与描述符绑定的IRemoteBroker对象。 |
| descriptor | string | 是 | 用于与IRemoteBroker对象绑定的描述符。 |

**示例**

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
let testRemoteObject = new TestRemoteObject('testObject');
```

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

查询接口描述符。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getDescriptor](arkts-ipc-rpc-iremoteobject-c.md#getdescriptor)()

<!--Device-RemoteObject-getInterfaceDescriptor(): string--><!--Device-RemoteObject-getInterfaceDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  let descriptor = testRemoteObject.getInterfaceDescriptor();
  hilog.info(0x0000, 'testTag', 'RpcServer: descriptor is: ' + descriptor);
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error ' + error);
}
```

## onRemoteRequest

```TypeScript
onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

sendRequest请求的响应处理函数，服务端在该函数里处理请求，回复结果。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [onRemoteMessageRequest](#onremotemessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

<!--Device-RemoteObject-onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-RemoteObject-onRemoteRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 对端发送的服务请求码。 |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 携带客户端调用参数的MessageParcel对象。 |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 写入结果的MessageParcel对象。 |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | 指示操作是同步还是异步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：操作成功，false：操作失败。 |

**示例**

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

**废弃版本：** 9

**替代接口：** [getLocalInterface](arkts-ipc-rpc-iremoteobject-c.md#getlocalinterface)(descriptor: string)

<!--Device-RemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker--><!--Device-RemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 需要查询的接口描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 如果接口描述符对应的远端对象存在，则返回该远端对象，否则返回Null。 |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  testRemoteObject.queryLocalInterface('testObject');
} catch (error) {
  hilog.error(0x0000, 'testTag', 'error: ' + error);
}
```

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收到回复，回复内容在reply报文里。

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

<!--Device-RemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-RemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 接收应答数据的MessageParcel对象。 |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：发送成功，false：发送失败。 |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString('hello');
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

<a id="sendrequest-1"></a>

## sendRequest

```TypeScript
sendRequest(
      code: number,
      data: MessageParcel,
      reply: MessageParcel,
      options: MessageOption
    ): Promise<SendRequestResult>
```

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

<!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>--><!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Request sending mode, which can be synchronous (default) or asynchronous. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Promise used to return the response to the request. |

**示例**

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
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString('hello');
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

<a id="sendrequest-2"></a>

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

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;)

<!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void--><!--Device-RemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | Request sending mode, which can be synchronous (default) or asynchronous. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | 是 | Callback for receiving the sending result. |

**示例**

```TypeScript
import { rpc } from '@kit.IPCKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

class TestRemoteObject extends rpc.RemoteObject {
  onRemoteRequest(code: number, data: rpc.MessageParcel, reply: rpc.MessageParcel,
    option: rpc.MessageOption): boolean {
    // 根据业务实际逻辑，进行相应处理
    return true;
  }
}
try {
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString('hello');
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
  let testRemoteObject = new TestRemoteObject('testObject');
  let option = new rpc.MessageOption();
  let data = rpc.MessageParcel.create();
  let reply = rpc.MessageParcel.create();
  data.writeInt(1);
  data.writeString('hello');
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
