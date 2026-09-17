# getSystemNetPortStates

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getSystemNetPortStates

```TypeScript
function getSystemNetPortStates(): Promise<NetPortStatesInfo>
```

Obtains information about all TCP and UDP ports currently listened by the system, and the PID and UID of the processes that listen for the ports. Both IPv4 and IPv6 addresses are supported.

> **NOTE:** 
> 
> This API is used to obtain information about the TCP and UDP ports currently listened by the system. The detailed
> fields are as follows:
> 
> TCP port fields: local address, local port, remote address, remote port, TCP connection status, process PID, and
> process UID
> 
> UDP port fields: local address, local port, process PID, and process UID

**Since:** 24

**Required permissions:** ohos.permission.GET_IP_MAC_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetPortStatesInfo](arkts-network-connection-netportstatesinfo-i.md)&gt; | Promise used to return the TCP and UDP port information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getSystemNetPortStates().then((data: connection.NetPortStatesInfo) => {
  console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  if (data.tcpPortStatesInfo?.length) {
    data.tcpPortStatesInfo?.forEach(item => {
      console.info(`Succeeded to get Tcp data: ${JSON.stringify(item)}`);
    })
  } else {
    console.info("TcpPortStatesInfo is undefined ");
  }
  if (data.udpPortStatesInfo?.length) {
    data.udpPortStatesInfo?.forEach(item => {
      console.info(`Succeeded to get Udp data: ${JSON.stringify(item)}`);
    })
  } else {
    console.info("UdpPortStatesInfo is undefined ");
  }
}).catch((error: BusinessError) => {
  console.error(`Error fetching getSystemNetPortStates. Code:${error.code}, message:${error.message}`);
});
```
