# NetHandle

```TypeScript
export interface NetHandle
```

Represents the network handle.

Before invoking **NetHandle** APIs, call **getNetHandle** to obtain a **NetHandle** object. For example, you can call [getDefaultNet](arkts-network-connection-getdefaultnet-f.md) to obtain the network handle of the default network.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bindSocket

```TypeScript
bindSocket(socketParam: TCPSocket | UDPSocket, callback: AsyncCallback<void>): void
```

Binds the TCPSocket or UDPSocket to the network specified by **NetHandle**. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socketParam | [TCPSocket](arkts-network-connection-tcpsocket-t.md) &#124; [UDPSocket](arkts-network-connection-udpsocket-t.md) | Yes | **TCPSocket** or **UDPSocket** object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the **TCPSocket** or **UDPSocket** object is successfully bound to the current network, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

  connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error('bind fail');
        return;
      }
      netHandle.bindSocket(tcp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info(JSON.stringify(data));
        }
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.info("on message, message:" + value.message + ", remoteInfo:" + value.remoteInfo);
    };
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info("Succeeded to get data: " + JSON.stringify(data));
      });
      netHandle.bindSocket(udp, (error: BusinessError, data: void) => {
        if (error) {
          console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
          return;
        } else {
          console.info(JSON.stringify(data));
        }
      });
    });
  }
})
```

<a id="bindsocket-1"></a>

## bindSocket

```TypeScript
bindSocket(socketParam: TCPSocket | UDPSocket): Promise<void>
```

Binds the TCPSocket or UDPSocket to the network specified by **NetHandle**. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socketParam | [TCPSocket](arkts-network-connection-tcpsocket-t.md) &#124; [UDPSocket](arkts-network-connection-udpsocket-t.md) | Yes | **TCPSocket** or **UDPSocket** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface Data {
  message: ArrayBuffer,
  remoteInfo: socket.SocketRemoteInfo
}

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let tcp : socket.TCPSocket = socket.constructTCPSocketInstance();
  let udp : socket.UDPSocket = socket.constructUDPSocketInstance();
  let socketType = "TCPSocket";
  if (socketType == "TCPSocket") {
    tcp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: Error) => {
      if (error) {
        console.error('bind fail');
        return;
      }
      netHandle.bindSocket(tcp).then(() => {
        console.info("bind socket success");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  } else {
    let callback: (value: Data) => void = (value: Data) => {
      console.info("on message, message:" + value.message + ", remoteInfo:" + value.remoteInfo);
    }
    udp.bind({address:"192.168.xxx.xxx",
              port:8080,
              family:1} as socket.NetAddress, (error: BusinessError) => {
      if (error) {
        console.error(`Failed to bind. Code:${error.code}, message:${error.message}`);
        return;
      }
      udp.on('message', (data: Data) => {
        console.info("Succeeded to get data: " + JSON.stringify(data));
      });
      netHandle.bindSocket(udp).then(() => {
        console.info("bind socket success");
      }).catch((error: BusinessError) => {
        console.error(`Failed to bind socket. Code:${error.code}, message:${error.message}`);
      });
    });
  }
});
```

## getAddressByName

```TypeScript
getAddressByName(host: string, callback: AsyncCallback<NetAddress>): void
```

Obtains the first IP address by using the network specified by **NetHandle** to resolve the host name. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt; | Yes | Callback used to return the result. If the first IP address is obtained successfully, **error** is **undefined**, and **data** is the first obtained IP address. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressByName(host, (error: BusinessError, data: connection.NetAddress) => {
    if (error) {
      console.error(`Failed to get address. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

<a id="getaddressbyname-1"></a>

## getAddressByName

```TypeScript
getAddressByName(host: string): Promise<NetAddress>
```

Obtains the first IP address by using the network specified by **NetHandle** to resolve the host name. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt; | Promise used to return the first IP address. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressByName(host).then((data: connection.NetAddress) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

## getAddressesByName

```TypeScript
getAddressesByName(host: string, callback: AsyncCallback<Array<NetAddress>>): void
```

Obtains all IP addresses by using the network specified by **NetHandle** to resolve the host name. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt;&gt; | Yes | Callback used to return the result. If all IP addresses are successfully obtained, **error** is **undefined**, and **data** is the list of all obtained IP addresses. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host, (error: BusinessError, data: connection.NetAddress[]) => {
    if (error) {
      console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

<a id="getaddressesbyname-1"></a>

## getAddressesByName

```TypeScript
getAddressesByName(host: string): Promise<Array<NetAddress>>
```

Obtains all IP addresses by using the network specified by **NetHandle** to resolve the host name. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt;&gt; | Promise used to return all IP addresses. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host).then((data: connection.NetAddress[]) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```

## getAddressesByNameWithOptions

```TypeScript
getAddressesByNameWithOptions(host: string, option?: QueryOptions): Promise<Array<NetAddress>>
```

Performs DNS resolution using the network specified by **NetHandle** based on the specified IP address type. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.INTERNET

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to resolve. For example, www.example.com. |
| option | [QueryOptions](arkts-network-connection-queryoptions-i.md) | No | Type of the IP address to be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt;&gt; | Promise used to return the queried IP address. In the command output, the port field has a fixed value of 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // If no network is connected, the obtained netId of netHandle is 0, which is abnormal. You can add specific processing based on the service requirements.
    return;
  }
  let host = "www.example.com";
  let option: connection.QueryOptions = {
      family: connection.FamilyType.FAMILY_TYPE_IPV4
    };
  netHandle.getAddressesByNameWithOptions(host, option).then((data: connection.NetAddress[]) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`get ERROR msg: ${JSON.stringify(err)}`)
  });
});
```

## netId

```TypeScript
netId: number
```

Network ID. The value **0** indicates that there is no default network. The other valid values must be greater than or equal to **100**.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core
