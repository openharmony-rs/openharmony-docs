# createNetConnection

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## createNetConnection

```TypeScript
function createNetConnection(netSpecifier?: NetSpecifier, timeout?: number): NetConnection
```

Creates a **NetConnection** object, which can be used to listen for the network status. [netSpecifier](arkts-network-connection-netspecifier-i.md) specifies the network to be listened for, and **timeout** indicates the timeout duration (ms). **netSpecifier** is a mandatory parameter for **timeout**. If neither of them is present, the default network is used.

> **NOTE:** 
> 
> To listen for the network status, after creating a **NetConnection** object, you need to call
> [register](arkts-network-connection-netconnection-i.md#register) to register the notification of the specified network status
> change.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netSpecifier | [NetSpecifier](arkts-network-connection-netspecifier-i.md) | No | Specification of the network to be listened for. If this parameter is not specified, the default network is listened for. |
| timeout | number | No | Timeout interval for obtaining the network specified by **netSpecifier**. The input value must be an uint32_t integer. This parameter is valid only when **netSpecifier** is present. The default value is **0**.<br>**Note:**  If the network to be listened for does not exist, the system attempts to activate the network. If the timeout interval is exceeded and the network status listener is registered, the **netUnavailable** event is triggered. |

**Return value:**

| Type | Description |
| --- | --- |
| [NetConnection](arkts-network-connection-netconnection-i.md) | Type of the network connection object to be listened for. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

// Example 1: Only the default network is concerned. You do not need to specify the netSpecifier parameter. If the timeout parameter is not passed, the timeout interval is not used. In this case, the value of timeout is 0.
let netConnection = connection.createNetConnection();

// Example 2: Only the cellular network is concerned. You need to specify the network type to cellular.
let timeout = 1000;
let netConnectionCellular = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_CELLULAR]
  }
}, timeout);

// Example 3: Both the cellular and Wi-Fi networks are concerned. You need to specify the network type to cellular and Wi-Fi.
let netConnectionCellularAndWifi = connection.createNetConnection({
  netCapabilities: {
    bearerTypes: [connection.NetBearType.BEARER_CELLULAR,
      connection.NetBearType.BEARER_WIFI]
  }
});
```
