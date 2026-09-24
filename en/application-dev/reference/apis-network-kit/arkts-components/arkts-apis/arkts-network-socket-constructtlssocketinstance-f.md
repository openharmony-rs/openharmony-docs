# constructTLSSocketInstance

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTLSSocketInstance

```TypeScript
function constructTLSSocketInstance(): TLSSocket
```

Creates a **TLSSocket** object.

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | **TLSSocket** object. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
```


<a id="constructtlssocketinstance-1"></a>

## constructTLSSocketInstance

```TypeScript
function constructTLSSocketInstance(tcpSocket: TCPSocket): TLSSocket
```

Upgrades a **TCPSocket** connection to a **TLSSocket** connection.

> **NOTE:** 
> 
> Before calling **constructTLSSocketInstance**, ensure that a **TCPSocket** connection has been established and no
> data is transmitted. After a successful upgrade, you do not need to call the **close** API for the **TCPSocket**
> object.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tcpSocket | [TCPSocket](arkts-network-socket-tcpsocket-i.md) | Yes | **TCPSocket** connection to be upgraded. |

**Return value:**

| Type | Description |
| --- | --- |
| [TLSSocket](arkts-network-socket-tlssocket-i.md) | **TLSSocket** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-system-internal-error) | System internal error. |
| 2303601 | Invalid socket FD. |
| 2303602 | Socket is not connected. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}

tcp.connect(tcpconnectoptions, (err: BusinessError) => {
  if (err) {
    console.error('connect fail');
    return;
  }
  console.info('connect success');

  // Ensure that a TCPSocket connection has been established before upgrading it to a TLSSocket connection.
  let tls: socket.TLSSocket = socket.constructTLSSocketInstance(tcp);
})
```
