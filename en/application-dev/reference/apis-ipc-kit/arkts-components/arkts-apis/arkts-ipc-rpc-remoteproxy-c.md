# RemoteProxy

Provides APIs to implement **IRemoteObject**.

**Inheritance/Implementation:** RemoteProxy extends [IRemoteObject](arkts-ipc-rpc-iremoteobject-c.md)

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## Modules to Import

```TypeScript
import { rpc } from '@kit.IPCKit';
```

## addDeathRecipient

```TypeScript
addDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

Adds a callback for receiving death notifications of the remote object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [registerDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#registerdeathrecipient)(recipient: DeathRecipient, flags: number)

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to add. |
| flags | number | Yes | Flag of the death notification. This parameter is reserved. It is set to **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the callback is added successfully; returns **false** otherwise. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, addDeathRecipient() of the proxy object is called to add a callback for receiving the death notification of the remove object.
```

## getDescriptor

```TypeScript
getDescriptor(): string
```

Obtains the interface descriptor (which is a string) of this object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Interface descriptor obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1900007](../errorcode-rpc.md#1900007-failed-to-communicate-with-the-remote-object) | communication failed. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, getDescriptor() of the proxy object is called to obtain the interface descriptor of the object.
```

## getInterfaceDescriptor

```TypeScript
getInterfaceDescriptor(): string
```

Obtains the interface descriptor of this proxy object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getDescriptor](arkts-ipc-rpc-iremoteobject-c.md#getdescriptor)()

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Interface descriptor obtained. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, getInterfaceDescriptor() of the proxy object is called to obtain the interface descriptor of the current proxy object.
```

## getLocalInterface

```TypeScript
getLocalInterface(interfaceDes: string): IRemoteBroker
```

Obtains the **LocalInterface** object of an interface token.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| interfaceDes | string | Yes | Interface descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | Returns **Null** by default, which indicates a proxy interface. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | check param failed |
| [1900006](../errorcode-rpc.md#1900006-ipc-object-permission-error) | Operation allowed only for the remote object. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, getLocalInterface() of the proxy object is called to obtain the interface descriptor.
```

## isObjectDead

```TypeScript
isObjectDead(): boolean
```

Checks whether the **RemoteObject** is dead.

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if **RemoteObject** is dead; returns **false** otherwise. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, isObjectDead() of the proxy object is called to check whether this object is dead.
```

## queryLocalInterface

```TypeScript
queryLocalInterface(interface: string): IRemoteBroker
```

Obtains the **LocalInterface** object of an interface token.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getLocalInterface](arkts-ipc-rpc-iremoteobject-c.md#getlocalinterface)(descriptor: string)

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| interface | string | Yes | Interface descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [IRemoteBroker](arkts-ipc-rpc-iremotebroker-i.md) | Returns **Null** by default, which indicates a proxy interface. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, queryLocalInterface() of the proxy object is called to obtain the interface descriptor.
```

## registerDeathRecipient

```TypeScript
registerDeathRecipient(recipient: DeathRecipient, flags: number): void
```

Registers a callback for receiving death notifications of the remote object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to register. |
| flags | number | Yes | Flag of the death notification. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, registerDeathRecipient() of the proxy object is called to register a callback for receiving the death notification of the remote object.
```

## removeDeathRecipient

```TypeScript
removeDeathRecipient(recipient: DeathRecipient, flags: number): boolean
```

Removes the callback used to receive death notifications of the remote object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [unregisterDeathRecipient](arkts-ipc-rpc-iremoteobject-c.md#unregisterdeathrecipient)(recipient: DeathRecipient, flags: number)

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to remove. |
| flags | number | Yes | Flag of the death notification. This parameter is reserved. It is set to **0**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the callback is removed; returns **false** otherwise. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, removeDeathRecipient() of the proxy object is called to remove the callback used to receive the death notification of the remote object.
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

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendMessageRequest** is returned, and the reply message contains the returned information.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object holding the data to send. |
| reply | [MessageSequence](arkts-ipc-rpc-messagesequence-c.md) | Yes | **MessageSequence** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RequestResult](arkts-ipc-rpc-requestresult-i.md)&gt; | Promise used to return a **requestResult** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.Failed to obtain the passed object instance. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendMessageRequest() of the proxy object is called to send a message.
```

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

Sends a **MessageSequence** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked at certain time after the response to **RequestResult** is returned, and the reply contains the returned information.

**Since:** 9

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

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendMessageRequest() of the proxy object is called to send a message.
```

## sendRequest

```TypeScript
sendRequest(code: number, data: MessageParcel, reply: MessageParcel, options: MessageOption): boolean
```

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

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

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendRequest() of the proxy object is called to send a message.
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

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a promise will be fulfilled immediately and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a promise will be fulfilled when the response to **sendRequest** is returned, and the reply message contains the returned information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption)

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
| Promise&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Promise used to return a **sendRequestResult** instance. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendRequest() of the proxy object is called to send a message.
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

Sends a **MessageParcel** message to the remote process in synchronous or asynchronous mode. If asynchronous mode is set in **options**, a callback will be called immediately, and the reply message is empty. The specific reply needs to be obtained from the callback on the service side. If synchronous mode is set in **options**, a callback will be invoked when the response to **sendRequest** is returned, and the reply message contains the returned information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sendMessageRequest](arkts-ipc-rpc-iremoteobject-c.md#sendmessagerequest)(code: number, data: MessageSequence, reply: MessageSequence, options: MessageOption, callback: AsyncCallback&lt;RequestResult&gt;)

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Message code [1-16777215] called by the request, which is determined by the communication parties. If the method is generated by an IDL tool, the message code is automatically generated by the IDL tool. |
| data | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object holding the data to send. |
| reply | [MessageParcel](arkts-ipc-rpc-messageparcel-c.md) | Yes | **MessageParcel** object that receives the response. |
| options | [MessageOption](arkts-ipc-rpc-messageoption-c.md) | Yes | Request sending mode, which can be synchronous (default) or asynchronous. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SendRequestResult](arkts-ipc-rpc-sendrequestresult-i.md)&gt; | Yes | Callback for receiving the sending result. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, sendRequest() of the proxy object is called to send a message.
```

## unregisterDeathRecipient

```TypeScript
unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void
```

Unregisters from the callback used to receive death notifications of the remote object.

**Since:** 9

**System capability:** SystemCapability.Communication.IPC.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recipient | [DeathRecipient](arkts-ipc-rpc-deathrecipient-i.md) | Yes | Callback to unregister. |
| flags | number | Yes | Flag of the death notification. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The number of parameters is incorrect; 2.The parameter type does not match; 3.The callback used to receive remote object death notifications is empty. |
| [1900008](../errorcode-rpc.md#1900008-invalid-ipc-object) | The proxy or remote object is invalid. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.getUIContext().getHostContext() is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

```TypeScript
The proxy object in the onConnect callback can be assigned a value only after the ability is connected asynchronously. Then, unregisterDeathRecipient() of the proxy object is called to unregister the callback for receiving the death notification of the remote object.
```

## DUMP_TRANSACTION

```TypeScript
static readonly DUMP_TRANSACTION: number
```

Internal instruction code used to obtain IPC service status information.

**Type:** number

**Default:** 1598311760

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## INTERFACE_TRANSACTION

```TypeScript
static readonly INTERFACE_TRANSACTION: number
```

Internal instruction code used to obtain the remote interface token.

**Type:** number

**Default:** 1598968902

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## MAX_TRANSACTION_ID

```TypeScript
static readonly MAX_TRANSACTION_ID: number
```

Maximum valid instruction code.

**Type:** number

**Default:** 0x00FFFFFF

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## MIN_TRANSACTION_ID

```TypeScript
static readonly MIN_TRANSACTION_ID: number
```

Minimum valid instruction code.

**Type:** number

**Default:** 0x1

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

## PING_TRANSACTION

```TypeScript
static readonly PING_TRANSACTION: number
```

Internal instruction code used to test whether the IPC service is normal.

**Type:** number

**Default:** 1599098439

**Since:** 7

**System capability:** SystemCapability.Communication.IPC.Core

**Test API:** This API is used only in automated test scripts.
