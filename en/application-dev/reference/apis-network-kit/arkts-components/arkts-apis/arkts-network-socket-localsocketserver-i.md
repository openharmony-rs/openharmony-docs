# LocalSocketServer

Defines a local socket server connection. Before calling LocalSocketServer APIs, you need to call [socket.constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md) to create a **LocalSocketServer** object.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(): Promise<void>
```

Stops listening for events of the **LocalSocketServer** object and releases the port bound by [listen](#listen). This API uses a promise to return the result.

> **NOTE:** 
> 
> This API does not close existing connections. To close the connection, call the [close] (#close11-1) API of
> [LocalSocketConnection] (#localsocketconnection11).

**Since:** 20

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-system-internal-error) | System internal error. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## getExtraOptions

```TypeScript
getExtraOptions(): Promise<ExtraOptionsBase>
```

Obtains the socket properties of the **LocalSocketServer** object. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<string>
```

Obtains the local socket address of a **LocalSocketServer** connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-system-internal-error) | System internal error. |
| [2301009](../errorcode-net-socket.md#2301009-bad-file-descriptor) | Bad file descriptor. |
| [2303188](../errorcode-net-socket.md#2303188-socket-operations-on-non-sockets) | Socket operation on non-socket. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

Obtains the file descriptor bound to the LocalSocketServer listening port. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This method can be called only after the [listen](#listen) method is successfully called.
> 
> - This API returns **-1** in abnormal cases such as listening exceptions or socket closed (for example, after close is called).
> 
> - The lifecycle of the file descriptor is managed by the system. The application can use the [close](arkts-network-socket-tcpsocketserver-i.md#close) method to close the socket connection, instead of directly operating the file descriptor.

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the socket file descriptor. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## getState

```TypeScript
getState(): Promise<SocketStateBase>
```

Obtains the status of a local socket server connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | Promise used to return the result. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## listen

```TypeScript
listen(address: LocalAddress): Promise<void>
```

Binds the address of the local socket file. The server listens to and accepts local socket connections established over the socket. Multiple threads are used to process client data concurrently. This API uses a promise to return the result.

> **NOTE:** 
> 
> The server uses this API to complete the **bind**, **listen**, and **accept** operations. If the address of the
> local socket file is passed for binding, a socket file is automatically created when this API is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | [LocalAddress](arkts-network-socket-localaddress-i.md) | Yes | Destination address. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, no value is returned. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2303109](../errorcode-net-socket.md#2303109-error-file-number) | Bad file number. |
| [2301013](../errorcode-net-socket.md#2301013-insufficient-permissions) | Insufficient permissions. |
| 2301022 | Invalid argument. |
| 2301098 | Address already in use. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## off('connect')

```TypeScript
off(type: 'connect', callback?: Callback<LocalSocketConnection>): void
```

Unsubscribes from **connect** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type.<br> 'connect': connection event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md)&gt; | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from **error** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: error event. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

## on('connect')

```TypeScript
on(type: 'connect', callback: Callback<LocalSocketConnection>): void
```

Subscribes to **connect** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type.<br> **connect**: connection event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to **error** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: error event. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

## setExtraOptions

```TypeScript
setExtraOptions(options: ExtraOptionsBase): Promise<void>
```

Sets the socket properties of the **LocalSocketServer** object. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md) | Yes | Other properties of the **LocalSocketServer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2301009](../errorcode-net-socket.md#2301009-bad-file-descriptor) | Bad file descriptor. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```
