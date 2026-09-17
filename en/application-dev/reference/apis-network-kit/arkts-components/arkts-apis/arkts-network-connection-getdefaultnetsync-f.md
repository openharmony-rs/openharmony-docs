# getDefaultNetSync

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDefaultNetSync

```TypeScript
function getDefaultNetSync(): NetHandle
```

Obtains the network handle used by the system by default, including the network ID. This API returns the result synchronously.

> **NOTE:** 
> 
> - Default network used by the system. The network must have the [NET_CAPABILITY_INTERNET](arkts-network-connection-netcap-e.md) capability and is not a VPN network.
> 
> - The return value of this interface is determined by the system and is irrelevant to whether the application specifies a network.
> 
> - Generally, the priority is as follows: Ethernet (PC) | Bluetooth (watch)Wi-Fi Cellular. In special cases,the actual returned result prevails.
> 
> - [NetHandle](arkts-network-connection-nethandle-i.md) is the unique identifier of the network. If no network is available,
> **0** is returned. It can be used by [getNetCapabilities](arkts-network-connection-getnetcapabilities-f.md) to query more
> network information.
> **Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 9

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [NetHandle](arkts-network-connection-nethandle-i.md) | Network handle of the default network. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getDefaultNetSync();
```
