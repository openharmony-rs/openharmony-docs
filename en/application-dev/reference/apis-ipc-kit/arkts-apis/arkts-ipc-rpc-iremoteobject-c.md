# IRemoteObject

```TypeScript
abstract class IRemoteObject
```

Provides methods to query or obtain interface descriptors, add or delete death notifications, dump object status to specific files, and send messages.

**Since:** 7

<!--Device-rpc-abstract class IRemoteObject--><!--Device-rpc-abstract class IRemoteObject-End-->

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## getDescriptor

```TypeScript
getDescriptor(): string
```

Obtains the interface descriptor (which is a string) of this object.

**Since:** 9

<!--Device-IRemoteObject-getDescriptor(): string--><!--Device-IRemoteObject-getDescriptor(): string-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Interface descriptor obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

## getLocalInterface

```TypeScript
getLocalInterface(descriptor: string): IRemoteBroker
```

Obtains the string of the interface descriptor.

**Since:** 9

<!--Device-IRemoteObject-getLocalInterface(descriptor: string): IRemoteBroker--><!--Device-IRemoteObject-getLocalInterface(descriptor: string): IRemoteBroker-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | string | Yes | String of the interface descriptor. The length of the string must be less than 40960. |

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | **IRemoteBroker** object bound to the specified interface descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The string length is greater than or equal to 40960; 4.The number of bytes copied to the buffer is different from the length of the obtained string. |

## isObjectDead

```TypeScript
isObjectDead(): boolean
```

Checks whether this object is dead.

**Since:** 7

<!--Device-IRemoteObject-isObjectDead(): boolean--><!--Device-IRemoteObject-isObjectDead(): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the object is dead; returns **false** otherwise. |

## registerDeathRecipient

```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: number): void
```

Registers a callback for receiving death notifications of the remote object.

**Since:** 9

<!--Device-IRemoteObject-registerDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-IRemoteObject-registerDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to register. |
| flags | number | Yes | Flag of the death notification. This is a reserved parameter. Set it to **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc-object-permission-error) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

## sendMessageRequest

```TypeScript
sendMessageRequest(
      code: number,
      data: MessageSequence,
      reply: MessageSequence,
      options: MessageOption
    ): Promise<RequestResult>
```

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If the asynchronous mode is set in **options**, the response result is returned immediately and **reply** is empty. The specific response needs to be obtained from the callback on the service side. If the synchronous mode is set in **options**, the response result is returned when **sendMessageRequest** returns, and **reply** contains the response content. This API returns the result asynchronously through a promise.

**Since:** 9

<!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>--><!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption    ): Promise<RequestResult>-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object that stores the data to be sent. It can be used only after being created via the **create()** method and data is written into it. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object that receives the response. In asynchronous mode, **reply** does not contain any content. The specific response needs to be obtained from the callback on the service side. In synchronous mode, **reply** contains the response content. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | Promise used to return the response to the request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

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

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

**Since:** 9

<!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void--><!--Device-IRemoteObject-sendMessageRequest(      code: int,      data: MessageSequence,      reply: MessageSequence,      options: MessageOption,      callback: AsyncCallback<RequestResult>    ): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object holding the data to send. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | Yes | Callback for receiving the sending result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

## unregisterDeathRecipient

```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void
```

Unregisters from the callback used to receive death notifications of the remote object.

**Since:** 9

<!--Device-IRemoteObject-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void--><!--Device-IRemoteObject-unregisterDeathRecipient(recipient: DeathRecipient, flags: int): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to unregister. |
| flags | number | Yes | Flag of the death notification. This is a reserved parameter. Set it to **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900005](../errorcode-rpc.md#1900005-ipc-object-permission-error) | Operation allowed only for the proxy object. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

## addDeathRecipient

```TypeScript
addDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

Adds a callback for receiving death notifications of the remote object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** registerDeathRecipient(recipient: DeathRecipient, flags: number)

<!--Device-IRemoteObject-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-IRemoteObject-addDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to register. |
| flags | number | Yes | Flag of the death notification. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the callback is added successfully; returns **false** otherwise. |

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

Obtains the interface descriptor (which is a string) of this object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getDescriptor()

<!--Device-IRemoteObject-getInterfaceDescriptor(): string--><!--Device-IRemoteObject-getInterfaceDescriptor(): string-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Interface descriptor obtained. |

## queryLocalInterface

```TypeScript
queryLocalInterface(descriptor: string): IRemoteBroker
```

Obtains the string of the interface descriptor.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getLocalInterface(descriptor: string)

<!--Device-IRemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker--><!--Device-IRemoteObject-queryLocalInterface(descriptor: string): IRemoteBroker-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | string | Yes | Interface descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | **IRemoteBroker** object bound to the specified interface descriptor. |

## removeDeathRecipient

```TypeScript
removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

Removes the callback used to receive death notifications of the remote object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** unregisterDeathRecipient(recipient: DeathRecipient, flags: number)

<!--Device-IRemoteObject-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean--><!--Device-IRemoteObject-removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to unregister. |
| flags | number | Yes | Flag of the death notification. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the callback is removed; returns **false** otherwise. |

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If the asynchronous mode is set in **options**, the API returns immediately and **reply** is empty. If the synchronous mode is set in **options**, the response is returned when **sendRequest** returns, and **reply** contains the response content.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

<!--Device-IRemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean--><!--Device-IRemoteObject-sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the message is sent successfully; returns **false** otherwise. |

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

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If the asynchronous mode is set in **options**, the response result is returned immediately and **reply** is empty. The specific response needs to be obtained from the callback on the service side. If the synchronous mode is set in **options**, the response result is returned when **sendRequest** returns, and **reply** contains the response content. This API returns the result asynchronously through a promise.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

<!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>--><!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption    ): Promise<SendRequestResult>-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Promise used to return the response to the request. |

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

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. This API uses an asynchronous callback to return the result. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific response needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** sendMessageRequest(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;)

<!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void--><!--Device-IRemoteObject-sendRequest(      code: number,      data: MessageParcel,      reply: MessageParcel,      options: MessageOption,      callback: AsyncCallback<SendRequestResult>    ): void-End-->

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Yes | Callback for receiving the sending result. |
