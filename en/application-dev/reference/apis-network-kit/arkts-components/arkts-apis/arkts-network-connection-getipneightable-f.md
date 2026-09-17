# getIpNeighTable

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getIpNeighTable

```TypeScript
function getIpNeighTable(): Promise<Array<NetIpMacInfo>>
```

Obtains information about entries in the IP neighbor table of the local device, including IPv4 and IPv6 entries. Each entry contains an IP address, a MAC address, and a network adapter name. This API uses a promise to return the result.

> **NOTE:** 
> 
> This interface is used to obtain the cached data of the IP neighbor table, not the data of all connections on the
> LAN.
> 
> This API is used to check network exceptions and parse the mapping between IP addresses and MAC addresses.

**Since:** 22

**Required permissions:** ohos.permission.GET_NETWORK_INFO and ohos.permission.GET_IP_MAC_INFO

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[NetIpMacInfo](arkts-network-connection-netipmacinfo-i.md)&gt;&gt; | Promise used to return information about entries in the IP neighbor table. |

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

connection.getIpNeighTable().then((data: connection.NetIpMacInfo[]) => {
  if (data.length !== 0) {
    console.info(`ipAddress:${data[0].ipAddress}`);
    console.info(`ifaceName:${data[0].iface}`);
    console.info(`macAddress:${data[0].macAddress}`);
  }
}).catch((error: BusinessError) => {
  console.error(`error fetching ip neigh table. Code:${error.code}, message:${error.message}`);
});
```
