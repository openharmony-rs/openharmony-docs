# MulticastSocket

Defines a **MulticastSocket** connection. Before calling MulticastSocket APIs, you need to call [socket.constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md) to create a **MulticastSocket** object.

**Inheritance/Implementation:** MulticastSocket extends [UDPSocket](arkts-network-socket-udpsocket-i.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## addMembership

```TypeScript
addMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void
```

Adds a member to a multicast group. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The IP addresses used for multicast belong to a specific range, for example, 224.0.0.0 to 239.255.255.255.
> 
> A member in a multicast group can serve as a sender or a receiver. Data is transmitted in broadcast mode,
> regardless of the client or server.

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| multicastAddress | [NetAddress](arkts-network-socket-p.md) | Yes | Destination address. For details, see [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301022 | Invalid argument. |
| 2301088 | Not a socket. |
| 2301098 | Address in use. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.addMembership(addr, (err: Object) => {
  if (err) {
    console.error('add membership fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('add membership success');
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.addMembership(addr).then(() => {
  console.info('addMembership success');
}).catch((err: Object) => {
  console.error('addMembership fail');
});
```

## addMembership

```TypeScript
addMembership(multicastAddress: NetAddress): Promise<void>
```

Adds a member to a multicast group. This API uses a promise to return the result.

> **NOTE:** 
> 
> The IP addresses used for multicast belong to a specific range, for example, 224.0.0.0 to 239.255.255.255.
> 
> A member in a multicast group can serve as a sender or a receiver. Data is transmitted in broadcast mode,
> regardless of the client or server.

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| multicastAddress | [NetAddress](arkts-network-socket-p.md) | Yes | Destination address. For details, see [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |
| 2301098 | Address in use. |

**Examples**

See [addMembership](#addmembership)

## dropMembership

```TypeScript
dropMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void
```

Drops a member from a multicast group. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The IP addresses used for multicast belong to a specific range, for example, 224.0.0.0 to 239.255.255.255.
> 
> You can drop only a member that has been added to a multicast group by using
> [addMembership](#addmembership).

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| multicastAddress | [NetAddress](arkts-network-socket-p.md) | Yes | Destination address. For details, see [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |
| 2301098 | Address in use. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.dropMembership(addr, (err: Object) => {
  if (err) {
    console.error('drop membership fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('drop membership success');
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.dropMembership(addr).then(() => {
  console.info('drop membership success');
}).catch((err: Object) => {
  console.error('drop membership fail');
});
```

## dropMembership

```TypeScript
dropMembership(multicastAddress: NetAddress): Promise<void>
```

Drops a member from a multicast group. This API uses a promise to return the result.

> **NOTE:** 
> 
> The IP addresses used for multicast belong to a specific range, for example, 224.0.0.0 to 239.255.255.255.
> 
> You can drop only a member that has been added to a multicast group by using
> [addMembership](#addmembership).

**Since:** 11

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| multicastAddress | [NetAddress](arkts-network-socket-p.md) | Yes | Destination address. For details, see [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |
| 2301098 | Address in use. |

**Examples**

See [dropMembership](#dropmembership)

## getLoopbackMode

```TypeScript
getLoopbackMode(callback: AsyncCallback<boolean>): void
```

Obtains the loopback mode flag for multicast communication. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Use this API to check whether the loopback mode is enabled.
> 
> The value **true** indicates that the loopback mode is enabled, and the value **false** indicates the opposite.
> When the loopback mode is disabled, the host does not receive the multicast packets sent by itself.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the loopback mode is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getLoopbackMode((err: Object, value: Boolean) => {
  if (err) {
    console.error('get loopback mode fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('get loopback mode success, value: ' + JSON.stringify(value));
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getLoopbackMode().then((value: Boolean) => {
  console.info('loopback mode: ', JSON.stringify(value));
}).catch((err: Object) => {
  console.error('get loopback mode failed');
});
```

## getLoopbackMode

```TypeScript
getLoopbackMode(): Promise<boolean>
```

Obtains the loopback mode flag for multicast communication. This API uses a promise to return the result.

> **NOTE:** 
> 
> Use this API to check whether the loopback mode is enabled.
> 
> The value **true** indicates that the loopback mode is enabled, and the value **false** indicates the opposite.
> When the loopback mode is disabled, the host does not receive the multicast packets sent by itself.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the loopback mode is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

See [getLoopbackMode](#getloopbackmode)

## getMulticastTTL

```TypeScript
getMulticastTTL(callback: AsyncCallback<number>): void
```

Obtains the TTL for multicast packets. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> TTL is used to limit the maximum number of router hops for packet transmission on a network.
> 
> The value ranges from 0 to 255. The default value is **1**.
> 
> If the TTL value is **1**, multicast packets can be transmitted only to the host directly connected to the
> sender. If the TTL is set to a large value, multicast packets can be transmitted over a longer distance.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getMulticastTTL((err: Object, value: Number) => {
  if (err) {
    console.error('set ttl fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set ttl success, value: ' + JSON.stringify(value));
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getMulticastTTL().then((value: Number) => {
  console.info('ttl: ', JSON.stringify(value));
}).catch((err: Object) => {
  console.error('set ttl failed');
});
```

## getMulticastTTL

```TypeScript
getMulticastTTL(): Promise<number>
```

Obtains the TTL for multicast packets. This API uses a promise to return the result.

> **NOTE:** 
> 
> TTL is used to limit the maximum number of router hops for packet transmission on a network.
> 
> The value ranges from 0 to 255. The default value is **1**.
> 
> If the TTL value is **1**, multicast packets can be transmitted only to the host directly connected to the
> sender. If the TTL is set to a large value, multicast packets can be transmitted over a longer distance.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

See [getMulticastTTL](#getmulticastttl)

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

Obtains the file descriptor of the MulticastSocket. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This API can be called only after [bind](arkts-network-socket-udpsocket-i.md#bind) is successfully called.
> 
> - This API returns **-1** in abnormal cases such as bind exceptions or socket closed (for example, after close is called).
> 
> - The lifecycle of the file descriptor is managed by the system. The application can use the [close](arkts-network-socket-udpsocket-i.md#close) method to close the socket connection,instead of directly operating the file descriptor.

**Since:** 23

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the socket file descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let bindAddr: socket.NetAddress = {
    address: '192.168.xx.xxx',
    port: 8080
}
multicast.bind(bindAddr)
  .then(() => {
    console.info('bind success');
    multicast.getSocketFd().then((fd: number) => {
      console.info(`Socket FD: ${fd}`);
    }).catch((err: BusinessError) => {
      console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
    });
  }).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

## setLoopbackMode

```TypeScript
setLoopbackMode(flag: boolean, callback: AsyncCallback<void>): void
```

Sets the loopback mode flag for multicast communication. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Use this API to enable or disable the loopback mode. By default, the loopback mode is enabled.
> 
> The value **true** indicates that the host is allowed to receive the multicast packets sent by itself, and the
> value **false** indicates the opposite.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | boolean | Yes | Whether to enable the loopback mode. The value **true** means to enable the loopback mode, and the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setLoopbackMode(false, (err: Object) => {
  if (err) {
    console.error('set loopback mode fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set loopback mode success');
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setLoopbackMode(false).then(() => {
  console.info('set loopback mode success');
}).catch((err: Object) => {
  console.error('set loopback mode failed');
});
```

## setLoopbackMode

```TypeScript
setLoopbackMode(flag: boolean): Promise<void>
```

Sets the loopback mode flag for multicast communication. This API uses a promise to return the result.

> **NOTE:** 
> 
> Use this API to enable or disable the loopback mode. By default, the loopback mode is enabled.
> 
> The value **true** indicates that the host is allowed to receive the multicast packets sent by itself, and the
> value **false** indicates the opposite.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flag | boolean | Yes | Whether to enable the loopback mode. The value **true** means to enable the loopback mode, and the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301088 | Not a socket. |

**Examples**

See [setLoopbackMode](#setloopbackmode)

## setMulticastTTL

```TypeScript
setMulticastTTL(ttl: number, callback: AsyncCallback<void>): void
```

Sets the time to live (TTL) for multicast packets. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> TTL is used to limit the maximum number of router hops for packet transmission on a network.
> 
> The value ranges from 0 to 255. The default value is **1**.
> 
> If the TTL value is **1**, multicast packets can be transmitted only to the host directly connected to the
> sender. If the TTL is set to a large value, multicast packets can be transmitted over a longer distance.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ttl | number | Yes | TTL value. The value is of the number type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301022 | Invalid argument. |
| 2301088 | Not a socket. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let ttl = 8
multicast.setMulticastTTL(ttl, (err: Object) => {
  if (err) {
    console.error('set ttl fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set ttl success');
})
```

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setMulticastTTL(8).then(() => {
  console.info('set ttl success');
}).catch((err: Object) => {
  console.error('set ttl failed');
});
```

## setMulticastTTL

```TypeScript
setMulticastTTL(ttl: number): Promise<void>
```

Sets the TTL for multicast packets. This API uses a promise to return the result.

> **NOTE:** 
> 
> TTL is used to limit the maximum number of router hops for packet transmission on a network.
> 
> The value ranges from 0 to 255. The default value is **1**.
> 
> If the TTL value is **1**, multicast packets can be transmitted only to the host directly connected to the
> sender. If the TTL is set to a large value, multicast packets can be transmitted over a longer distance.
> 
> This API is effective only after
> [addMembership](#addmembership)
> is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ttl | number | Yes | TTL value. The value is of the number type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301022 | Invalid argument. |
| 2301088 | Not a socket. |

**Examples**

See [setMulticastTTL](#setmulticastttl)

## setReuseAddress

```TypeScript
setReuseAddress(reuse: boolean): void
```

Sets whether the multicast socket supports address reuse. This API is called in synchronous mode.

> **NOTE:** 
> 
> This API is used to control whether to enable address reuse when a multicast socket is bound to a port.
> 
> To bind an occupied port, ensure that the address reuse capability is enabled for the party that occupies the
> port. In addition, the service needs to call this API before calling
> [bind](arkts-network-socket-udpsocket-i.md#bind) to enable the address
> reuse capability.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reuse | boolean | Yes | Whether to enable address reuse. **true** to enable, **false** otherwise. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let bindAddr: socket.NetAddress = {
  // 0.0.0.0 indicates that port 8080 on all IPv4 network APIs of the local host is bound. This is commonly used to receive data from this port in multicast scenarios.
  address: '0.0.0.0',
  port: 8080
}

try {
  multicast.setReuseAddress(true);
  multicast.bind(bindAddr).then(() => {
    console.info('setReuseAddress success');
  }).catch((err: BusinessError) => {
    console.error(`bind failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`setReuseAddress failed, code is ${error.code}, message is ${error.message}`);
}
```
