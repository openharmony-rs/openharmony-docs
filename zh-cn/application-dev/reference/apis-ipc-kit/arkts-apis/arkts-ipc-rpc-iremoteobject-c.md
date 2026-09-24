# IRemoteObject

```TypeScript
abstract class IRemoteObject
```

该接口可用于查询或获取接口描述符、添加或删除死亡通知、转储对象状态到特定文件、发送消息。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.IPC.Core

## 导入模块

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## getDescriptor

```TypeScript
getDescriptor(): string
```

获取对象的接口描述符，接口描述符为字符串。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

## getLocalInterface

```TypeScript
getLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 9

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

## isObjectDead

```TypeScript
isObjectDead(): boolean
```

检查当前对象是否死亡。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：对象死亡，false：对象未死亡。 |

## registerDeathRecipient

```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: number): void
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | 是 | 要注册的回调。 |
| flags | number | 是 | 死亡通知标志。保留参数，设置为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc对象权限错误) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

## sendMessageRequest

```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

以同步或异步方式向对端进程发送MessageSequence消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结果将在sendMessageRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 保存待发送数据的MessageSequence对象，需先通过create()方法创建并写入数据后方可使用。 |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 接收应答数据的MessageSequence对象。异步模式下reply报文里没有内容，具体回复需在业务侧回调中获取；同步模式下回复内容在reply报文里。 |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | Promise对象，返回发送请求的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

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

以同步或异步方式向对端进程发送MessageSequence消息。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收到回调，回复内容在reply报文里。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 保存待发送数据的MessageSequence对象。 |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | 是 | 接收应答数据的MessageSequence对象。 |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | 是 | 回调函数。当消息发送成功时，可从RequestResult中读取服务端返回的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

## unregisterDeathRecipient

```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | 是 | 要注销的回调。 |
| flags | number | 是 | 死亡通知标志。保留参数，设置为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc对象权限错误) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

## addDeathRecipient

```TypeScript
addDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** registerDeathRecipient(recipient: DeathRecipient, flags: number)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | 是 | 要注册的回调。 |
| flags | number | 是 | 死亡通知标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注册成功，false：回调注册失败。 |

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

获取对象的接口描述符，接口描述符为字符串。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDescriptor()

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

## queryLocalInterface

```TypeScript
queryLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getLocalInterface(descriptor: string)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | 返回绑定到指定接口描述符的IRemoteBroker对象。 |

## removeDeathRecipient

```TypeScript
removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** unregisterDeathRecipient(recipient: DeathRecipient, flags: number)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | 是 | 要注销的回调。 |
| flags | number | 是 | 死亡通知标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注销成功，false：回调注销失败。 |

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即返回，reply报文里没有内容。如果为选项设置了同步模式，则将在sendRequest返回时收到回复，回复内容在reply报文里。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

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

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则发送请求的响应结果立即返回，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则发送请求的响应结果将在sendRequest返回时返回，回复内容在reply报文里。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

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
| Promise&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Promise对象，返回发送请求的响应结果。 |

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

以同步或异步方式向对端进程发送MessageParcel消息。使用callback异步回调。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回时收到回调，回复内容在reply报文里。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;)

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | 是 | 接收应答数据的MessageParcel对象。 |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | 是 | 接收发送结果的回调。 |
