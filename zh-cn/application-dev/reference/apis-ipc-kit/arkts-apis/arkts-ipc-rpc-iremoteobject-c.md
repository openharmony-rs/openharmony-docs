# IRemoteObject

该接口可用于查询或获取接口描述符、添加或删除死亡通知、转储对象状态到特定文件、发送消息。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-rpc-abstract class IRemoteObject--><!--Device-rpc-abstract class IRemoteObject-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

## addDeathRecipient

```TypeScript
addDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [registerDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#registerdeathrecipient)(recipient:

<!--Device-IRemoteObject-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-IRemoteObject-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注册的回调。 |
| flags | number | 是 | 死亡通知标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注册成功，false：回调注册失败。 |

## getDescriptor

```TypeScript
getDescriptor(): string
```

获取对象的接口描述符，接口描述符为字符串。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-getDescriptor(): string--><!--Device-IRemoteObject-getDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

获取对象的接口描述符，接口描述符为字符串。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getDescriptor](arkts-ipc-rpc-iremoteobject-c.md#getdescriptor)()

<!--Device-IRemoteObject-getInterfaceDescriptor(): string--><!--Device-IRemoteObject-getInterfaceDescriptor(): string-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回接口描述符。 |

## getLocalInterface

```TypeScript
getLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-getLocalInterface(descriptor: string): IRemoteBroker--><!--Device-IRemoteObject-getLocalInterface(descriptor: string): IRemoteBroker-End-->

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

## isObjectDead

```TypeScript
isObjectDead(): boolean
```

检查当前对象是否死亡。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-isObjectDead(): boolean--><!--Device-IRemoteObject-isObjectDead(): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：对象死亡，false：对象未死亡。 |

## queryLocalInterface

```TypeScript
queryLocalInterface(descriptor: string): IRemoteBroker
```

查询接口描述符的字符串。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getLocalInterface](arkts-ipc-rpc-iremoteobject-c.md#getlocalinterface)(descriptor:

<!--Device-IRemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker--><!--Device-IRemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | string | 是 | 接口描述符的字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回绑定到指定接口描述符的IRemoteBroker对象。 |

## registerDeathRecipient

ArkTS-Dyn:
```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: number): void
```

ArkTS-Sta:
```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: int): void
```

注册用于接收远程对象死亡通知的回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-registerDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-IRemoteObject-registerDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注册的回调。 |
| flags | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 死亡通知标志。保留参数，设置为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc对象权限错误) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

## removeDeathRecipient

```TypeScript
removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [unregisterDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#unregisterdeathrecipient)(recipient:

<!--Device-IRemoteObject-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-IRemoteObject-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注销的回调。 |
| flags | number | 是 | 死亡通知标志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：回调注销成功，false：回调注销失败。 |

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

<!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>--><!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageSequence对象，需先通过create()方法创建并写入数据后方可使用。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageSequence对象。异步模式下reply报文里没有内容，具体回复需在业务侧回调中获取；同步模式下回复内容在reply报文里。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RequestResult&gt; | Promise对象，返回发送请求的响应结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.Failed to obtain the passed object instance. |

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

以同步或异步方式向对端进程发送MessageSequence消息。如果为选项设置了异步模式，则立即收到回调，reply报文里没有内容，具体回复需要在业务侧的回调中获取。如果为选项设置了同步模式，则将在sendRequest返回 时收到回调，回复内容在reply报文里。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void--><!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void-End-->

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

以同步或异步方式向对端进程发送MessageParcel消息。如果为选项设置了异步模式，则立即返回，reply报文里没有内容。如果为选项设置了同步模式，则将在sendRequest返回时收到回复，回复内容在reply报文里。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-IRemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-IRemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

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

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>--><!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>-End-->

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

**替代接口：** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code:

<!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void--><!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 本次请求调用的消息码[1-16777215]，由通信双方确定。如果接口由IDL工具生成，则消息代码由IDL自动生成。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 保存待发送数据的MessageParcel对象。 |
| reply | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 接收应答数据的MessageParcel对象。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 本次请求的同异步模式，默认同步调用。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SendRequestResult&gt; | 是 | 接收发送结果的回调。 |

## unregisterDeathRecipient

ArkTS-Dyn:
```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void
```

ArkTS-Sta:
```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void
```

注销用于接收远程对象死亡通知的回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-IRemoteObject-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-IRemoteObject-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**系统能力：** SystemCapability.Communication.IPC.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recipient | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要注销的回调。 |
| flags | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 死亡通知标志。保留参数，设置为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.The number of parameters is incorrect;2.The parameter type does not match;3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc对象权限错误) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-非法的ipc对象) | The proxy or remote object is invalid. |

